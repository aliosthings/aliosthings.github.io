# 版本发布


### [1.2.1](https://github.com/alibaba/AliOS-Things/releases/tag/v1.2.1)

- [源代码 (zip) ](https://github.com/alibaba/AliOS-Things/archive/v1.2.1.zip)
- [源代码 (tar.gz)](https://github.com/alibaba/AliOS-Things/archive/v1.2.1.tar.gz)

亮点:
- SIG BLE Mesh
- Link Voice

v1.2.1 其他要点:
- MCU：支持 Cortex-M7, KL27，RL78, RX600
- 内核: 支持 yaffs2
- 协议栈: BLE 5.0
- 驱动: ST 6轴MEMS传感器 LSM6DSL, 气压传感器 LPS22HB
- 基础设施: 支持 Keil／IAR makefile

### [1.2.0](https://github.com/alibaba/AliOS-Things/releases/tag/v1.2.0)

- [源代码 (zip) ](https://github.com/alibaba/AliOS-Things/archive/v1.2.0.zip)
- [源代码 (tar.gz)](https://github.com/alibaba/AliOS-Things/archive/v1.2.0.tar.gz)

亮点:

- AOS API
- 基于 NXP LPC54102 支持 GT202 WiFi 模组 (高通 QCA4002)
- uData 框架和传感器驱动器
- uMesh 扩展认证协议 (ID²)
- 第一版 BLE 应用框架
- 在 ESP32 和 Nordic NF51822 上支持 BLE 协议栈 4.2 Preview 

v1.2.0 版本还主要增加了以下功能和支持 :

- MCU: LPC54102
- 开发板: LPC54102 Express, MK3239(BLE), MK1101
- 内核: CPU深度睡眠模式后的tick补偿，固定的缓冲器队列
- 协议栈: uMesh EAP(ID²), BLE 应用程序框架, BLE 协议栈 4.2
- 中间件: uData 框架, Bosch 传感器驱动器

### [1.1.2](https://github.com/alibaba/AliOS-Things/releases/tag/v1.1.2)

- [源代码 (zip)](https://github.com/alibaba/AliOS-Things/archive/v1.1.2.zip)
- [源代码 (tar.gz)](https://github.com/alibaba/AliOS-Things/archive/v1.1.2.tar.gz)

亮点:

- 支持Keil/IAR
- AliOS Things 测试套件
- 支持LoRaWAN 
- CK802T 可信运行环境(TEE)

v1.1.2版本还主要增加了以下功能和支持 :

- MCU: stm32l0xx, stm32l4xx, csky(ck802/ck802t)
- 开发板: STM32L073RZ-Nucleo, STM32L496GDiscovery, eml3047(LoRa), mk3166(WiFi), Hobbit(TEE)
- 内核: 优化定时器，优化任务删除
- 安全: CK802 可信运行环境(TEE)
- 协议栈: LoRaWAN, SAL(AT)
- 中间件: FOTA CoAP
- 设备: mk3060 SAL


### [1.1.1](https://github.com/alibaba/AliOS-Things/releases/tag/aos1.1.1)

- [源代码 (zip)](https://github.com/alibaba/AliOS-Things/archive/aos1.1.1.zip)
- [源代码 (tar.gz)](https://github.com/alibaba/AliOS-Things/archive/aos1.1.1.tar.gz)

v1.1.1版本主要增加了以下功能和支持 :

- 支持的新平台: ESP32 (WiFi，WiFi Mesh & BLE)
- AT 框架: 包括AT Parser, AT HAL
- IP模式的SAL: 基于AT的 socket APIs 
- 3 BINS: 内核，框架，应用程序
- JavaScript 引擎
- 测试环境基础组件,和 AliOS Studio 集成开发环境一起提供多设备的开发和调平台


### [1.1.0](https://github.com/alibaba/AliOS-Things/releases/tag/aos1.1.0)

- [源代码 (zip)](https://github.com/alibaba/AliOS-Things/archive/aos1.1.0.zip)
- [源代码 (tar.gz)](https://github.com/alibaba/AliOS-Things/archive/aos1.1.0.tar.gz)

第一次在Github发布。

AliOS Things的主要组件包括:

- VFS: 对于嵌入式系统的简单的虚拟文件系统
- KV: 针对闪存设备的密钥存储系统

- yloop: 简单但功能强大的框架来减少多线程的复杂性
- LWIP: 经过良好测试的TCP / IP协议栈，支持IPv4和IPv6

- uMesh: 内部开发的Mesh网络栈，可支持802.11，802.15.4，和BLE

- 安全组件: 包括安全传输层协议 （TLS）、可信框架服务（TFS）、可信执行环境（TEE）

- FOTA：端到端的提供FOTA解决方案
- 物联网协议：包括SDS；支持MQTT和CoAP

参考链接:

- AliOS Things 官方网站: <https://iot.aliyun.com/product/alios>
- SDS: <https://iot.aliyun.com/product/open>
- IoT 套件: <https://iot.aliyun.com/product/netsuite>
