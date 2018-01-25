## AliOS Things

> AliOS Things is Alibaba's IoT version of AliOS Family, it was announced in The Computing Conference 2017 in Hangzhou by Alibaba Cloud, and open sourced in 20<sup>th</sup>, October, 2017 at github: https://github.com/alibaba/AliOS-Things.

## Vision

AliOS Things targets to build the turnkey solution for IoT infrastructure, with the key abilities of performance, simplicity, security, cloud integration, rich components and so on.  
Further more, it natively supports the connection between devices and Aliyun Link, therefore can be widely applied in smart home, smart city, next-generation travel, etc.

See the [Quick start](quickstart.md) for more details.

## Architecture Overview

From an architectural point of view, AliOS Things adapts Layered Architecture and Component Architecture. From bottom to top, AliOS Things includes:

- BSP: Board Support Package mainly developed and maintained by SoC Vendor
- HAL: Hardware Abstraction Layer, like WiFi, UART
- Kernel: Rhino RTOS Kernel, Yloop, VFS, KV Storage included
- Protocol Stack: LwIP TCPIP Stack, uMesh mesh networking stack included
- Security: TLS, TFS(Trusted Framework Service), TEE(Trusted Exexcution Environment)
- AOS API: AliOS Things exposed APIs for Application and Middleware
- Middleware: Alibaba's value-added and commonly seen IoT components included
- Examples: hands-on sample codes, and well tested applications such as Alinkapp

All modules have been organized as Components, and each component has its own .mk file to describe its dependency with other Components, which enables applications to choose components needed easily.

### Quick Start by Command Line using Ubuntu Machine

```shell
$ pip install aos-cube
$ git clone https://github.com/alibaba/AliOS-Things.git
$ cd AliOS-Things
$ aos make helloworld@linuxhost
$ ./out/helloworld@linuxhost/binary/helloworld@linuxhost.elf
```

## Applications

Check out the [Showcase](/#) to AliOS Things in use.
