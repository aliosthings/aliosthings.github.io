# AliOS Things 网络适配框架 - SAL



**摘要**：很多物联网应用场景中，都需要使用主控MCU外接连接芯片（如WiFi、NB-IoT）的解决方案。为方便这类场景的开发，AliOS Things提供了Socket Adapter Layer（SAL）框架和组件方案。



AliOS Things中提供了丰富的SAL开发组件，来加速MCU+通信连接芯片的应用场景开发和部署。在此类应用场景中，主控MCU芯片通过UART或SPI总线与WiFi、NB-IoT等通信芯片相连，AliOS Things操作系统和用户APP运行在主控MCU中，需要网络数据访问时，通过外接的通信芯片进行网络负载的接收和发射。主控MCU和外接通信芯片之间的通信，可以是AT Command通道，也可以是厂商私有协议通道。

![at_scena2](https://img.alicdn.com/tfs/TB1pO7NmhSYBuNjSsphXXbGvVXa-374-397.png)

## AliOS Things SAL方案概述

目前，AliOS Things提供了atparser、at_adapter、SAL等开发组件。借助这些组件，用户可以方便地进行应用开发，同时这些组件也方便厂商在现有MCU产品基础上通过外接通信芯片方式扩展网络访问能力。下图展示了AliOS Things提供的SAL组件和方案架构：

![](https://img.alicdn.com/tfs/TB1CCjJmDtYBeNjy1XdXXXXyVXa-1372-1344.png)

其中，atparser组件提供了基础的AT Command访问接口和异步收发机制。用户可以直接访问atparser组件提供的接口进行应用开发。上层应用直接通过atparser访问网络是，需要自行处理AT命令细节。

基于atparser的基础上，AliOS Things进一步提供了Socket Adapter Layer（SAL）组件（即上图中的方案一）。SAL组件提供AT通道或厂商私有协议通道（如高通通信模组的WMI）到Socket套接字（如`socket`、`getaddrinfo`、`send`、`recvfrom`等）接口的对接。通过SAL组件，应用层不需要关注通信芯片底层操作的细节，只需要通过标准的Socket接口来达到访问网络的目的。SAL组件支持大多数常用的Socket接口。SAL组件可以很大程度上提高应用层开发的效率，显著降低应用层开发的难度。

此外，AliOS Things还提供了另外一种基于AT Command的网络访问方案 - SAL LwIP模式（即上图中的方案三）。SAL LwIP模式基于at_adapter组件工具。at_adapter组件提供AT底层到LwIP的对接，即AT通道作为LwIP的一个网络接口（netif）。使用该方案时，应用层通过标准的Socket接口访问网络，不需要关注底层AT细节。该方案无缝对接LwIP协议栈，应用层可以使用所有LwIP提供的接口和服务。但该方案需要连接芯片固件支持IP包收发模式，目前庆科的moc108已经支持该模式。

## atparser组件

atparser组件是AliOS Things SAL框架的基础组件之一，它提供统一和规范的AT命令访问接口（如`at.send`、`recv`、`write`、`read`、`oob`等）和异步收发机制（`at_worker`）。目前atparser组件仅支持了UART连接方式。

atparser有两种工作模式，即NORMAL模式和ASYN模式。工作模式的选择在atparser组件的初始化时进行。

NORMAL模式下，仅支持上层应用以单进程/线程方式访问AT（同一时刻只有一个进程访问AT）。由于AT底层通过串行方式（UART或其他）发送和接收数据，在多进程情况下，多个AT读写可能会产生数据交叉，从而造成AT访问的混乱及错误。下面是在NORMAL模式下，使用AT接口的示例（连接WiFi AP）：

```c
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

在ASYN模式下，支持AT命令的多进程访问以及收据的异步接收。系统中只有一个线程（`at_worker`）负责读取AT数据，发送线程发送完AT命令后，等待`at_worker`线程唤醒；`at_worker`线程接收到对应AT命令的结果数据后，将结果传递给发送线程，并唤醒发送线程继续执行。发送线程确保一个AT命令发送是原子操作。在ASYN模式下，可以支持多个进程对AT的访问。

AT事件的处理（例如网络数据到达），通过注册的oob回调函数处理。`at_worker`线程负责识别AT事件并通过调用`oob`回调函数处理AT事件和数据。

## Socket Adapter Layer (SAL)

SAL模块提供基于AT Command或厂商私有协议方案实现的标准Socket接口访问。下图是SAL（方案一）的架构图。

![img](https://img.alicdn.com/tfs/TB1fCaGmCtYBeNjSspaXXaOOFXa-1332-914.png)

SAL对上（应用层）提供标准Socket接口访问。目前SAL支持多数常用的Socket接口，后续还将持续演进。以下是SAL目前支持的Socket接口：

```c
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

SAL层对下抽象了通信模组/芯片访问控制层接口（如下），不同厂家的连接模组/芯片，可以通过对接底层控制访问层接口来对接和支持SAL。

```c
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

## SAL LwIP模式

AliOS Things还提供了SAL LwIP模式（方案二）。该方案区别于方案一的地方在于，主控MCU上运行完整的LwIP协议栈，LwIP协议栈底层通过AT方式访问网络；方案一中主控MCU侧不运行协议栈。

该方案的运行方式类似于MCU行业常用的SLIP（Serial Line Internet Protocol）方案，区别在于底层使用厂商模组/芯片的AT Command命令和服务，厂商模组/芯片不需要额外再支持SLIP通信。

at_adapter组件提供AT底层到LwIP网络接口（netif）的对接。通过netif的对接，AT通道可以无缝对接上LwIP。该模式下，SAL对上层应用提供完整的TCP/IP协议栈接口和服务。该方案的缺点是需要AT通信模块固件支持IP包传输，目前moc108已经支持该模式。

## 总结

综上所述，AliOS Things提供了丰富的AT组件和方案。AliOS Things提供的AT框架和组件，具有以下优势：

+ 为主控MCU外接连接芯片场景提供完整解决方案；
+ 可以降低上层应用开发基于AT场景的应用的难度，提高开发效率，加速产品部署；
+ 方便模组和设备厂商在现有成熟的MCU产品和方案上，通过AT方式扩展网络连接能力，而不需要将先有的MCU芯片切换成WiFi或其他具有网络通信能力的平台。
