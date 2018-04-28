# Release

### [1.2.2](https://github.com/alibaba/AliOS-Things/releases/tag/v1.2.2)

- [source code (zip) ](https://github.com/alibaba/AliOS-Things/archive/v1.2.2.zip)
- [source code (tar.gz)](https://github.com/alibaba/AliOS-Things/archive/v1.2.2.tar.gz)

Special version for [AliOS Things Starter Kit](starterkit) support.

### [1.2.1](https://github.com/alibaba/AliOS-Things/releases/tag/v1.2.1)

- [source code (zip) ](https://github.com/alibaba/AliOS-Things/archive/v1.2.1.zip)
- [source code (tar.gz)](https://github.com/alibaba/AliOS-Things/archive/v1.2.1.tar.gz)

Highlights:
- SIG BLE Mesh Preview
- Link Voice Preview

Other major enhancements included in v1.2.1:
- MCU：Cortex-M7, KL27，RL78, RX600
- Kernel: yaffs2 support
- Protocols: BLE 5.0
- Drivers: STM A+G combo sensor LSM6DSL, pressure sensor LPS22HB
- Infrastructure: Keil／IAR makefile support

### [1.2.0](https://github.com/alibaba/AliOS-Things/releases/tag/v1.2.0)

- [source code (zip) ](https://github.com/alibaba/AliOS-Things/archive/v1.2.0.zip)
- [source code (tar.gz)](https://github.com/alibaba/AliOS-Things/archive/v1.2.0.tar.gz)

Highlights:
* AOS API
* NXP LPC54102 with GT202(Qualcomm QCA4002)
* uData Framework and Sensor Drivers
* uMesh EAP(ID²)
* BLE Application Framework Initial Version
* BLE Stack 4.2 Preview supporting ESP32 and Nordic NF51822

Other major enhancements included in v1.2.0:
* MCU: LPC54102
* Board LPC54102 Express, MK3239(BLE), MK1101
* Kernel: Tick Compensation from Deep Sleep, Fixed Buffer Queue
* Protocol Stack: uMesh EAP(ID2), BLE Application Framework, BLE Stack 4.2
* Middleware: uData Framework, Bosch Sensor Drivers

### [1.1.2](https://github.com/alibaba/AliOS-Things/releases/tag/v1.1.2)

- [source code (zip)](https://github.com/alibaba/AliOS-Things/archive/v1.1.2.zip)
- [souce code (tar.gz)](https://github.com/alibaba/AliOS-Things/archive/v1.1.2.tar.gz)

Highlights:
- Keil/IAR support
- AliOS Things Testsuite
- LoRaWAN support
- CK802T TEE(Trust Execution Environment)

Other major enhancements included in v1.1.2:
- MCU: stm32l0xx, stm32l4xx, csky(ck802/ck802t)
- Board: STM32L073RZ-Nucleo,STM32L496GDiscovery,eml3047(LoRa),mk3166(WiFi),Hobbit(TEE)
- Kernel: Timer refine, Task deletion refine
- Security: CK802 TEE
- Protocol Stack: LoRaWAN, SAL(AT)
- Middleware: FOTA CoAP
- Device: mk3060 SAL

### [1.1.1](https://github.com/alibaba/AliOS-Things/releases/tag/aos1.1.1)

- [source code (zip)](https://github.com/alibaba/AliOS-Things/archive/aos1.1.1.zip)
- [source code (tar.gz)](https://github.com/alibaba/AliOS-Things/archive/aos1.1.1.tar.gz)

Major enhancements included in v1.1.1:
- New platform supported: ESP32 (WiFi，WiFi Mesh & BLE)
- AT framework, including: AT Parser, AT HAL
- Socket Adaption Layer(IP Mode): socket APIs over AT
- 3 BINS: kernel/framwork/app
- JavaScript Engine
- Testbed infrastructure, working with AliOS Studio IDE to provide enhanced multi-device develop/debug capability

### [1.1.0](https://github.com/alibaba/AliOS-Things/releases/tag/aos1.1.0)

- [source code (zip)](https://github.com/alibaba/AliOS-Things/archive/aos1.1.0.zip)
- [source code (tar.gz)](https://github.com/alibaba/AliOS-Things/archive/aos1.1.0.tar.gz)

First release at Github.

Major components included in AliOS Things are:
- Rhino, an in-house developed RTOS kernel
- VFS, simple virtual file system for embedded system
- KV, key-value storage system targeted flash devices
- Yloop, simple yet powerful framework to reduce overhead and complexity of multi-threading
- LWIP, well tested tcp/ip stack, both IPv4 and IPv6 supported
- uMesh, in-house developed mesh networking stack, 802.11, 802.15.4, and BLE supported
- Security components included: TLS, TFS(Trusted Framework Service), TEE(Trusted Execution Environment)
- FOTA, end-to-end FOTA service
- IoT Protocols including SDS, MQTT, CoAP are supported

Reference:
- AliOS Things official site: https://iot.aliyun.com/product/alios
- SDS: https://iot.aliyun.com/product/open
- IoT Suite: https://iot.aliyun.com/product/netsuite
