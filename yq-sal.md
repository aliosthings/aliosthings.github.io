## AliOS Things Socket Adapter Layer (SAL) 

*Abstract：* In many IoT application scenarios, communication chips need to be externally connected to MCU (such as WiFi、NB-IoT). To make the development of this kind of scenarios more easily, AliOS Things has provided Socket Adapter Layer (SAL) framework and related components. 

AliOS Things has provided rich SAL development components to accelerate the development of MCU + communication chips scenarios. In such scenarios, MCU is connected to communication chips such as WiFi and NB-IoT through UART or SPI line. The operating system of AliOS Things and users' APP are operated in MCU, and when network data access is needed, receiving and transmitting of network load can be enabled through externally-connected communication chips. The communication between MCU and communication chips can be realized through AT Command channel or other private protocol channels.

![at_scena2](https://img.alicdn.com/tfs/TB1pO7NmhSYBuNjSsphXXbGvVXa-374-397.png)

## AliOS Things SAL framework overview 

AliOS Things has provided development components such as `atparser`、`at_adapter` and `SAL`. With these components, users can carry out development easily. Meanwhile, vendors can improve their network access ability based on current MCU products. The following picture shows the SAL components and plans provided by AliOS Things :

![](https://img.alicdn.com/tfs/TB1CCjJmDtYBeNjy1XdXXXXyVXa-1372-1344.png)

Among them, `atparser` provides basic AT Command access interfaces and asynchronous transceiver mechanism. Users can directly use the interfaces provided by `atparser` for application development. If upper layer applications want to connect to network directly through `atparser`, you need to modify AT command.

Based on atparser, AliOS Things has further provided SAL components (Plan 1 in the above picture). SAL components can provide AT channels or vendors private protocol channels (such as WMI provided by Qualcomm), so that application layer no longer needs to pay attention to how communication chips operate in bottom layer. Instead, it only needs standard Socket interfaces to connect to network. SAL can support most of commonly-used Socket interfaces and can greatly improve the efficiency and reduce the difficulty of application layer development.

In addition, AliOS Things has also provided a network access plan based on AT Command--SAL LwIP mode (plan 3 in the above picture). It's designed based on a component tool called `at_adapter`. It enables the connection between AT bottom layer and LwIP, where AT channel is used as a network interface (`netif`). When using this plan, application layer access to network through standard Socket interfaces. This plan is seamlessly connected to LwIP protocol stack, and application layer can use all the interfaces and services provided by LwIP. But this plan requires communication chips to support IP transceiver mode. At present, moc108 provided by Mxchip has supported this mode.

## Atparser 

Atparser is one of the basic components in AliOS Things SAL framework. It has provided unified and standardized AT command access interfaces (such as `at.send`、`recv`、`write`、`read`、`oob`) and asynchronous transceiver mechanism (`at_worker`). At present, atparser can only support UART connection.

Atparser has two working modes--NORMAL mode and ASYN mode. Working mode can be selected during atparser initialization.

In NORMAL mode, upper layer applications can only have access to AT by single process / thread mode (only one process can access AT at the same time). Since AT bottom layer sends and receives data through serial mode (UART or other), in multiple processes, multiple AT reads and writes may produce data crossover, resulting in error in AT access. The following code is an example of using AT interface in NORMAL mode (connecting to WiFi AP) :

```
if (at.send("AT+WJAP=test_AP,test_passwd") == false) {
  printf("at.send failed.\r\n");
  return -1;
}
// Read AT cmd response right after a cmd is sent
if (at.recv("OK") == false) {
  printf("Connecting AP failed.\r\n");
  return -1
}

```

ASYN mode can support multi-process access to AT command and asynchronous information reception. In this system, only one thread (`at_worker`) is responsible for reading AT data. After sending thread sends out AT command, it will wait for at_worker to wake up. When at_worker receives the result data of corresponding AT command, it will passes the result to sending thread, and wakes up it to continue execution. Sending threads ensures that the sending of AT commands is executed by atom operation. Under ASYN mode, multiple processes can be supported to access AT at the same time.

The handling of AT events (such as network data arrivals) is processed by registered `oob` callback function. At_worker can identify AT events and process them by calling oob.

## SAL

SAL provides standard Socket interfaces based on AT Command or vendor private protocols. The following picture is the architecture of SAL (plan 1).

![img](https://img.alicdn.com/tfs/TB1fCaGmCtYBeNjSspaXXaOOFXa-1332-914.png)

SAL provides standard Socket interfaces to application layer. It can now support most commonly used Socket interfaces, and more will be supported in the future. The following are the Socket interfaces that SAL has currently supported :

```
int select(int maxfdp1, fd_set *readset, fd_set *writeset,
           fd_set *exceptset, struct timeval *timeout);
int socket(int domain, int type, int protocol);
int write(int s, const void *data, size_t size);
int connect(int s, const struct sockaddr *name, socklen_t namelen);
int bind(int s, const struct sockaddr *name, socklen_t namelen);
int eventfd(unsigned int initval, int flags);
int setsockopt(int s, int level, int optname,
               const void *optval, socklen_t optlen);
int getsockopt(int s, int level, int optname,
               void *optval, socklen_t *optlen);
struct hostent* gethostbyname(const char *name);
int close(int s);
int sendto(int s, const void * data, size_t size, int flags,
           const struct sockaddr * to, socklen_t tolen);
int send(int s, const void *data, size_t size, int flags);
int shutdown(int s, int how);
int recvfrom(int s, void *mem, size_t len, int flags,
             struct sockaddr *from, socklen_t *fromlen);
int recv(int s, void *mem, size_t len, int flags);
int read(int s, void *mem, size_t len);
void freeaddrinfo(struct addrinfo *ai);
int getaddrinfo(const char *nodename, const char *servname,
                const struct addrinfo *hints, struct addrinfo **res);
void freeaddrinfo(struct addrinfo *ai);
int shutdown(int s, int how);
int getaddrinfo(const char *nodename, const char *servname,
                const struct addrinfo *hints, struct addrinfo **res);
int fcntl(int s, int cmd, int val);

```

SAL has abstracted the communication modules / chips interfaces connected to control layer (as follows). Connection modules / chips from different vendors can access SAL through these interfaces.

```
typedef struct sal_op_s {
    char *version;
    int (*init)(void);
    int (*start)(at_conn_t *c);
    int (*send)(int fd, uint8_t *data, uint32_t len,
                char remote_ip[IP_LEN], int32_t remote_port);
    int (*domain_to_ip)(char *domain, char ip[IP_LEN]);
    int (*close)(int fd, int32_t remote_port);
    int (*deinit)(void);
    int (*register_netconn_evt_cb)(netconn_evt_cb_t cb);
} sal_op_t;

```

## SAL LwIP mode

AliOS Things has also provided SAL LwIP mode (plan 2). Its difference from plan 1 is that whole LwIP protocol stack is run in MCU, and LwIP protocol stack has access to network through AT. By contrast, in plan 1, protocol stack will not run in MCU side.

The operation of this plan is similar to SLIP (Serial Line Internet Protocol). The difference lies in that no extra SLIP communication support is needed when bottom layer using AT commands and services provided by vendor modules / chips.

At_adapter supports docking of AT bottom layer with LwIP network interface (netif). Through netif, AT channel can seamlessly connect to LwIP. In this mode, SAL provides a complete TCP/IP protocol stack interface and service for upper applications. But this plan requires communication chips to support IP transceiver mode. At present, moc108 provided by Mxchip has supported this mode.

## Summary

To sum up, AliOS Things provides rich SAL components and plans. It has the following advantages:

- It provides a complete solution for scenarios that need communication chips to externally linked to MCU. 

- It can greatly improve the efficiency and reduce the difficulty for application layer development.

- It enables vendors to improve their network connecting ability based on current MCU products and plans. 
