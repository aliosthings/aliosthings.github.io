# AliOS Things Developer Kit

Developer Kit 是 AliOS Things 官方出品的高阶开发板，提供了比 [Starter Kit](zh-ch/starterkit.md) 更加丰富的资源。

在传感器方面，除了惯导类加速度计、陀螺仪以外，还提供了大量环境感知类器件如磁力计、气压计、温湿度传感器、红外传感器以及接近光传感器，可以为各类物联网业务场景提供云端一体化集成的方案验证。

在硬件接口能力方面该款开发板资源也首屈一指，USB OTG, SD Card, Mini PCIe, Arduino shield 接口等等均有支持。另外板上集成 MCU 外挂 WiFi 模组方案，通过 SAL(Socket Adapt Layer) 为应用开发和数据上云提供了极简途径。

和 Starter Kit 一样，用户可以直接使用板载 ST-LINK V2 进行固件烧录和调试。

快速开始：[使用 AliOS Studio 开发 Developer Kit](https://github.com/alibaba/AliOS-Things/wiki/Developer-Kit-Tutorial)

## 特性

- MCU: [STM32L496VG](http://www.st.com/en/microcontrollers/stm32l496vg.html), LQFP 100, Cortex-M4 80MHz
- Memory: 1MB Flash, 320KB SRAM
- Micro-USB: USB 2.0, USB1 for ST-Link, USB2 for OTG
- Sensors: 3D Accelerometer, Gyrometer, Magnetometer, Pressure sensor, Humidity and Temperature sensor, IR detector and emitter, ALS and Proximity sensor
- Camera: 640*480 pixels
- Key: 1 reset key, 3 user keys
- LED: 1 RGB LED, 3 user LEDs
- LCD: 1.3’’ TFT, 240x240 pixels
- Wi-Fi Module: 802.11 b/g/n, Easy-link
- Audio: Headphone, Mic, Speech recognition
- SD card: Support 32GB
- OS: AliOS Things

## 产品图片

![](https://img.alicdn.com/tfs/TB122RCtntYBeNjy1XdXXXXyVXa-2373-3121.png)

![](https://img.alicdn.com/tfs/TB1hAjQsY9YBuNjy0FgXXcxcXXa-2381-3143.png)

## 详细参数

| **项目**                      | **描述**                                                     | **规格**                                                     |
| ----------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| MCU Information               | CPU                                                          | STM32L496VG, ARM Contex-M4, 80MHz                            |
|                               | Memory                                                       | 320KB SRAM, 1MB internal Flash                               |
| Display                       | LCD                                                          | 1.3', 240*240, SPI                                           |
|                               | LED                                                          | 1 RGB LED, 1 Power LED(Green), 1 Program LED(Orange), 3 status LED(Orange) |
| Sensors                       | Accelerator                                                  | Support                                                      |
|                               | Gyrometer                                                    | Support                                                      |
|                               | Magnetometer                                                 | Support                                                      |
|                               | Pressure Sensor                                              | Support                                                      |
|                               | Humidity & Temperature Sensor                                | Support                                                      |
|                               | IR detector and emitter                                      | Support                                                      |
|                               | ALS and Proximity sensor                                     | Support                                                      |
|                               | Camera                                                       | 640*480 pixels                                               |
| Power features                | Power Interface                                              | micro USB                                                    |
|                               | Working Voltage                                              | DC 4.2-12V (typical5V)                                       |
| Audio                         | Codec                                                        | I2S, I2C                                                     |
|                               | Mic                                                          | Analog Differential Mic                                      |
|                               | Headset                                                      | 3.5mm connector                                              |
| Interface                     | micro USB1                                                   | USB2.0, for download and debug                               |
|                               | micro USB2                                                   | USB2.0, OTG                                                  |
|                               | Uart                                                         | for Wifi, Zigbee, Lora, NB                                   |
|                               | I2C                                                          | for sensors                                                  |
|                               | SPI                                                          | for LCM                                                      |
|                               | Key                                                          | Reset Key, Function Key x 3                                  |
|                               | T-Flash                                                      | Support up to 32GB                                           |
|                               | mini PCIe                                                    | 2G, 4G                                                       |
|                               | Arduino R3 DuPont interface                                  |                                                              |
| Wifi Module                   | Protocol                                                     | 802.11 b/g/n                                                 |
|                               | SOC                                                          | Contex M4 100MHz, 128kB RAM                                  |
|                               |                                                              | 512kB on-chip flash + 2MB on board flash                     |
|                               | Operating Voltage                                            | DC 3-3.6V ( (typical3.3V))                                   |
| Environmental Characteristics | Standard working temperature                                 | -10℃ ~ +45℃                                                  |
|                               | Operating humidity                                           | 5%～95% (non-condensing)                                     |
| Dimension                     | 100*75mm                                                     |                                                              |
| OS                            | AliOS Things                                                 |                                                              |
| Application                   | Wireless control, Wireless sensor, Audio decode, G-sensor Games... |                                                       ||
