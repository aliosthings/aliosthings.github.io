## Brief Probe into Features of IoT Network

Abstrace: Network is of vital importance to IoT devices. This article talks about some features of IoT network, and shows what solutions have AliOS Things provided. The features of  IoT network includes IP network, UDP network, multiple means of communication and topologies. Based on them, AliOS Things have provided CoAP, SAL and uMesh to meet the demands.

### IP network

![图1 互联网全球连接快照图](https://img.alicdn.com/tfs/TB1DUoUjY_I8KJjy1XaXXbsxpXa-640-640.jpg)

Nowadays is a diverse age when all technology has a variety of standards competing with each other. From this perspective, the existence of IP network is a miracle. IP network is an unified world, providing a good foundation for interconnection of all things. Zigbee has launched Zigbee IP, Google has launched Thread based on 802.15.4; Silicon Labs, TI and other Zigbee core vendors have also worked on it. (Thread used by Nest is developed by Silicon).

IP network can also bring several obvious benefits to IoT.

- There are many mature software stacks on IP, such as security component TLS/DTLS.
- IPv6 can provide enough address space.
- A large number of software developers familiar with socket.


Of course, IP only provides a channel, and protocols in upper layer are needed. There have been ICA alliance in Ali cloud, OCF, Google Weave and HomeKit. 

### UDP network

There are mainly two transportation layer protocols on IP: TCP and UDP. TCP is obviously more popular than UDP since TCP/IP is generally heard rather than UDP/IP.

TCP is a reliable transportation layer protocol based on byte stream. It is a good choice for applications with good network environment and low real-time requirements, such as HTTP in Web era. However, gradually, TCP handshake protocol has become a bottleneck for many Web APIs. Google, for example, has proposed QUIC (Quick UDP Internet Connection), trying to improve users' experience through UDP.

In IoT age, the problem of TCP is more prominent, because IoT is characterized with bad network signal, limited bandwidth and power consumption. NB-IoT is a typical example. Most NB-IOT terminals work in battery environment, with low transmission rate and varied application scenarios. TCP's connection oriented and timeout retransmission mechanism consumes more memory and affects power consumption.

Imagine the procedure when sensors upload data: collect data, report data and sleep. The mechanism to keep alive and retransmit will reduce battery life and consume more memory.

Currently, the popular channel protocol in cloud is still based on TCP, mainly MQTT, including Ali cloud IoT suite, Amazon and Azure. However, Ali cloud IoT suite also supports CoAP, and Google Weave mainly uses UDP as a means of communication.

### Multiple means of communication

The speed, coverage, reliability, power consumption, deployment and cost of different communication technologies are different, and no one is totally the best. 3G/4G network is superior to WiFi in coverage, but inferior to it in terms of speed, power and cost. WiFi is superior to BLE in rate, but BlE is better in power consumption.

In IoT field, LPWA (Low Power Wide Area) technology NB-IoT, LoRa, SigFox are widely used. Their low power and wide coverage feature simplifies the deployment in a variety of complex environments. WSN (Wireless Sensor Network) technology based on 802.15.4, Zigbee and Wi-Sun, have obvious advantages in power and cost, and is suitable for large-scale deployment.

WiFi/BLE applications have attracted wide attention with its popularity in consumer electronics. Because WiFi doesn't need gateway, it is favored by various home appliances manufacturers. (However, when number of intelligent devices at home keeps increasing, AP connections will become a bottleneck). Meanwhile, WiFi Alliance for IoT launched a low power version 802.11ah (Wi-Fi HaLow) in 2016, and BLE 5.0 has faster rate, larger MTU, better point-to-point communication experience and enables construction of WSN based on BLE, which poses a threat to existing technologies such as Zigbee.

![图3 一种典型的WSN架构](https://img.alicdn.com/tfs/TB1jGj9j9_I8KJjy0FoXXaFnVXa-554-262.png)

## Multiple means of communication and topology

The following picture shows common network topologies :
![图2 网络拓扑](https://img.alicdn.com/tfs/TB1Zvp2hOqAXuNjy1XdXXaYcVXa-406-199.png)

In Ethernet, Tree and Bus topology are the most common. LAN is a Bus topology internally, but when connecting to Internet, it needs to pass through the gateway, which can be viewed as a root node of the tree, so it is also a Tree topology. In wireless LAN, WiFi is Star topology, and WSN is mainly Tree/Mesh. In Wan, including LPWA, it can be regarded as Star topology based on base station, and Mesh topology between base stations.

Based on the existing backbone network built on Ethernet, we believe that WSN/LPWA will be applied more and more frequently in IoT field. WSN's low cost, low power consumption feature together with LPWA's low power and wide coverage can cover a wide range of IoT scenarios.

## Features of AliOS Things network

Based on the above features, in addition to a highly optimized protocol stack, AliOS Things provides corresponding components to meet the demands :

### Full link optimization based on CoAP

AliOS Things supports the channel to the cloud based on CoAP (such as the Ali cloud IoT suite), and supports CoAP-based FOTA, making it possible to build a full UDP system.

![img](https://img.alicdn.com/tfs/TB1MpWUj8fH8KJjy1XbXXbLdXXa-655-332.png)

### SAL

It's common for IoT devices to externally connect communication modules with MCU, and the communication methods between them are varied. In order to reduce the complexity, TCP/IP protocol stack is often completely run on communication modules, and MCU controls it by AT or private protocols. Based on it, AliOS Things provides standard socket interfaces to the upper layer through SAL, and adapts private protocols according to SAL device. For AT modules, AT Parser further reduces the complexity of docking. 

### uMesh

UMesh is a self-organized network protocol stack under IP and above MAC. It's a routing Mesh that supports tree topology and mesh topology, and the structured address routing under tree topology greatly reduces the size of routing tables. UMesh can seamlessly connect to TCP/IP protocol stack, enables resource-limited wireless devices to connect to IP network easily. It's designed for complex network to complete the communication in last mile.

## Summary

This article talks about some features of IoT network and corresponding components in AliOS Things. You can visit <https://github.com/alibaba/AliOS-Things> to build a better IoT OS with us. 
