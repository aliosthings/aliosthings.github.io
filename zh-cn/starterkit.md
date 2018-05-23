# AliOS Things Starter Kit

Starter Kit是为AliOS Things量身打造的开发板，提供了丰富的板上资源，包含板级传感器，LCD屏幕（240\*240），Audio，板上WiFi模块。AliOS Things是 AliOS 家族旗下的、面向IoT领域的、高可伸缩的物联网操作系统，详情请见 [AliOS Things](https://github.com/alibaba/AliOS-Things)

AliOS Things Starter Kit板上集成了ST-LINK V2，用户无需额外花费外接调试器。

围绕AliOS Things Starter Kit阿里还提供了一套免费，极简的开发工具alios-studio，基于该工具用户可以完成从编译到烧录到调试的完整的IDE开发环境。  

详见：[使用 AliOS Studio 开发 Starter Kit](https://github.com/alibaba/AliOS-Things/wiki/Starter-Kit-Tutorial)

## 特性

- MCU: STM32L433CCT6, 48LQFP, Cortex-M4, 80MHz
- Memory: 256KB Flash, 64KB RAM
- USB: micro-USB, 5V Power Supply
- Sensors: Accelerator, Light-Sensor
- LCD: 240*240 Pixels, 1.3" TFT
- Key: 4 User Buttons
- LED: 1RGB LED, 2 Status LED
- Audio: Headphone, Mic, Codec
- WiFi Module: 802.11 b/g/n, Easy-Link
- On-board ST-LINK/V2-1 debugger
- OS: AliOS Things

## 产品图片

![](https://img.alicdn.com/tfs/TB1_KoTiFmWBuNjSspdXXbugXXa-3704-2422.jpg)

## 详细参数

| **项目**                      | **描述**                                                     | **规格**                                                     |
| ----------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| CPU information               | CPU                                                          | STM32L433CCT6  ARM Contex-M4,80MHz                           |
|                               | Memory                                                       | 64KB SRAM,256kB internal Flash                               |
| Display                       | LCD                                                          | 1.3', 240*240, SPI                                           |
|                               | LED                                                          | 1xRGB, 1 Power LED(Green), 1 Program LED(orange), 2 status LED(Orange) |
| Sensors                       | Accelerator                                                  | Support                                                      |
|                               | Light-Sensor                                                 | Support                                                      |
| Power features                | Power Interface                                              | microUSB                                                     |
|                               | Working Voltage                                              | DC 4.2-12V (typical5V)                                       |
| Audio                         | Codec                                                        | I2S,                                                         |
|                               | Speaker                                                      | 0.5-1W                                                       |
|                               | Mic                                                          | Analog Differential Mic                                      |
| Interface                     | USB                                                          | USB2.0, for download and debug                               |
|                               | Uart                                                         | for Wifi                                                     |
|                               | I2C                                                          | for sensors                                                  |
|                               | SPI                                                          | for LCM                                                      |
|                               | Key                                                          | Reset Key, Function Key x 3                                  |
| Wifi Module                   | Protocol                                                     | 802.11b/g/n                                                  |
|                               | SOC                                                          | Contex M4 100MHz, 128kB RAM                                  |
|                               |                                                              | 512kB on-chip flash + 2MB on board flash                     |
|                               | Operating Voltage                                            | DC 3-3.6V ( (typical3.3V))                                   |
| Environmental Characteristics | standard working temperature                                 | -10 ℃～+45℃                                                  |
|                               | Operating humidity                                           | 5%～95% (non-condensing)                                     |
| Dimension                     | 70*80mm                                                      |                                                              |
| OS                            | AliOS Things                                                 |                                                              |
| Application                   | Wireless control, Wireless sensor, Audio decode, G-sensor Games... | | |

## GUI 示例

![](https://img.alicdn.com/tfs/TB17EnugqmWBuNjy1XaXXXCbXXa-484-387.gif)
