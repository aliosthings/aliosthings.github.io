# 关于IoT网络的一些特征的探讨

网络是IoT设备非常关键的部分,本文和大家一起探讨IoT网络的几个重要特征，及AliOS Things尝试提供的一些解决方案。
<br>

## IP网络

![图1 互联网全球连接快照图](https://img.alicdn.com/tfs/TB1DUoUjY_I8KJjy1XaXXbsxpXa-640-640.jpg)

今天是一个多样化的时代，不管什么技术都有多种标准存在，明争暗斗，每个人都有自己的小算盘，想要形成一个大一统的标准非常困难。从这个角度来说，IP网络的存在是个奇迹。IP网络真正做到了无种族，无国界，即插即用。IP网络可以为万物互联提供一个很好的基础。这种趋势也越来越明显，Zigbee推出了Zigbee IP，而谷歌也推出了同样基于802.15.4的Thread，Silicon Labs，TI等Zigbee核心厂商也纷纷支持（谷歌收购的Nest所使用的Thread是Silicon Labs开发的）。

IP网络还能给物联网带来几个明显的好处：

- IP之上有大量成熟的软件栈，比如安全组件TLS/DTLS
- IPv6能提供足够多的地址空间
- 大量熟悉socket的软件开发人员

当然IP只是提供了一个通道，还需要有上层的协议来做保证“彼此听得懂”，现在比较流行的有阿里云的ICA联盟，OCF，Google Weave，HomeKit的存在，这个话题在此不展开。
<br>

## UDP网络

IP之上主要的两个传输层协议：TCP和UDP。应该说，目前为止，TCP都是碾压UDP的，一般听到的都是TCP/IP，几乎没听过UDP/IP。

TCP是一种面向连接的，可靠的，基于字节流的传输层协议。TCP的保活/重传/拥塞控制提供了一个很好的性能/健壮性折衷，对网络环境较好，实时性要求不高的应用来说，比如Web时代最流行的HTTP，TCP是非常好的选择。但是慢慢开始有人觉得TCP做得太多了，TCP的握手协议成为很多的Web API的性能的瓶颈，比如谷歌提出了QUIC（Quick UDP Internet Connection）试图通过UDP来进一步提高用户的网络体验。

在物联网，TCP的问题就更突出了，因为物联网环境经常面临网络信号不好，带宽有限，功耗苛刻。最近风头正劲的NB-IoT就是一个典型的例子。大多数NB-IOT的终端设备工作在电池环境下，传输速率较低，应用场景多种多样。TCP的面向连接，超时重传机制消耗更多的内存，同时也影响了功耗。

设想一下常见的传感器定时上传数据的场景：采集数据，上报数据，睡眠。因为定时上报，很多情况下，偶尔丢失数据是可以接受的。但是TCP为了提高数据到达率，其保活和重传机制会降低电池寿命，同时重传机制会消耗内存。

目前主流的云端通道协议还是基于TCP，主要是MQTT，包括阿里云IoT套件，Amazon，Azure。而[阿里云IoT套件](https://help.aliyun.com/document_detail/57697.html?spm=5176.100239.blogcont309562.12.vn0LZB)也支持CoAP，Google Weave也主要采用了UDP作为通信手段。
<br>

## 多种通信技术并存

不同的通信技术，其速率，覆盖范围，可靠性，功耗，部署，成本都是不同的，没有一种技术能包治百病。3G/4G网络在覆盖范围上优于WiFi，但是在速率，功耗，成本上又不如WiFi。WiFi在速率上秒杀BLE，但是功耗又被BLE秒杀。

物联网领域，LPWA（Low Power Wide Area）技术NB-IoT，LoRa，SigFox受到广泛关注，其低功耗广覆盖的特点，简化了各种复杂环境下的部署。基于802.15.4的WSN(Wireless Sensor Network)[3]技术Zigbee，Wi-Sun，在功耗和成本优势明显，适合大规模部署。

WiFi/BLE在消费电子类的普及度，其应用受到广泛关注。WiFi由于不需要网关，受到各种家电厂商的青睐（但是家里的智能设备越来越多时，AP的连接数将成为瓶颈）。同时，面向物联网WiFi联盟于2016年推出了WiFi的低功耗版本，802.11ah（Wi-Fi HaLow）[4]。BLE随着5.0的推出，更快的速率，更大的mtu，除了提高现有的点到点通信体验，基于BLE构建WSN也变得可能，对Zigbee等现有技术构成了威胁。

![图3 一种典型的WSN架构](https://img.alicdn.com/tfs/TB1jGj9j9_I8KJjy0FoXXaFnVXa-554-262.png)
<br>

## 多种连接方式及网络拓扑并存

下图是常见的网络拓扑：
![图2 网络拓扑](https://img.alicdn.com/tfs/TB1Zvp2hOqAXuNjy1XdXXaYcVXa-406-199.png)

图1 互联网全球连接快照图，可以隐约看出一棵棵树的存在。在以太网中，Tree和Bus较为常见，有线局域网内部是一个Bus拓扑，但是从访问互联网的角度，需要经过网关，网关就成为了树的根节点，所以也是一种Tree拓扑。而在无线局域网中，WiFi是Star拓扑，WSN以Tree/Mesh为主。在广域网包括LPWA，可以看作以基站为主的Star拓扑，基站之间则是Mesh拓扑。

在现有的以太网构成的骨干网基础上，在物联网中相信WSN/LPWA会有越来越多的应用。WSN的低成本低功耗，配合LPWA的低功耗广覆盖，可以覆盖非常广的物联网场景。
<br>

## AliOS Things的网络特性

针对上述的特点，AliOS Things从多个纬度提供相应的组件以更好的支持IoT设备的网络需求。除了基于LwIP2.0高度优化的协议栈外，还提供了以下丰富的组件：

### 基于CoAP的全链路优化

AliOS Things支持基于CoAP的上云通道（比如阿里云IoT套件），同时支持基于CoAP的FOTA，使得构建一个全UDP的系统成为可能。关于AliOS Things上的CoAP支持的进一步信息可以参考：[AliOS Things全链路优化-CoAP FOTA](https://yq.aliyun.com/articles/309562)。

![](https://img.alicdn.com/tfs/TB1MpWUj8fH8KJjy1XbXXbLdXXa-655-332.png)

### SAL网络适配层

在IoT设备上MCU外挂通信模块非常常见，而MCU和通信模块之间的通信方式也多种多样，为了降低复杂度，经常是通信模块上跑了完整的TCP/IP协议栈，而MCU通过AT或者私有协议去控制。针对这种情况，AliOS Things通过SAL组件，对上层提供标准socket接口，对下则可以基于SAL device适配私有协议。对于常见的AT模块，AT Parser进一步降低了对接的复杂度。进一步信息参考：[AliOS Things网络适配框架 - SAL](https://yq.aliyun.com/articles/292612?spm=5176.100239.0.0.ndirf0)。

### uMesh

uMesh是无线协议无关的，IP之下，MAC之上的自组织网络协议栈。uMesh是一种Routing Mesh，支持树状拓扑和网状拓扑，树状拓扑下采用结构化地址路由，极大的减少了路由表大小。uMesh可以无缝和TCPIP协议栈对接，从而使得各类资源受限的无线设备可以简单的接入IP网络。uMesh是AliOS Things为复杂网络设计的，解决最后一公里通信问题的技术。

## 总结

本文探讨了IoT网络的一些特征，及AliOS Things的一些相应特性，欢迎访问AliOS Things github官网：https://github.com/alibaba/AliOS-Things，和我们一起构建一个更好的面向物联网的操作系统。
<br>

## 引用

[1][Computer Network](https://en.wikipedia.org/wiki/Computer_network)
[2][Network Topology](https://en.wikipedia.org/wiki/Network_topology)
[3][WSN](https://en.wikipedia.org/wiki/Wireless_sensor_network)
[4][802.11ah](https://en.wikipedia.org/wiki/IEEE_802.11ah)
[5][M2M with UDP](http://www.embedded.com/design/real-world-applications/4426378/Speed-up-machine-to-machine-networking-with-UDP)
