# AliOS Things Developer Kit

Developer Kit is brought to you by AliOS Things, aims at advanced development. It offers much richer resources compared with [Starter Kit](starterkit.md).

As regards sensors, apart from commonly known inertial measurement sensors including accelerometer and gyro, it also integrates all kinds of environment sensing devices such as magnetometer, barometer, humidity & temperature sensor, IR detector & emitter, ALS and Proximity sensor. Accordingly, solutions for different IoT application scenarios can be tested and verified based on this platform.

Further more, the hardware interfaces offered by Developer Kit are rich enough for various purpose, as for instance, USB OTG, SD Card, Mini PCIe are all provided, even with Arduino shield interfaces. On the other hand, standalone WiFi module is integrated, making it much easier for cloud based application development, thanks to SAL(Socket Adapt Layer) software module.

Same as Starter Kit, it's straight forward for developers to do firmware uploading and debugging by accessing the on-board ST-LINK V2.

Quick start: [Launch Developer Kit with AliOS Studio](https://github.com/alibaba/AliOS-Things/wiki/Developer-Kit-Tutorial)

## Features

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

## Snapshot

![](https://img.alicdn.com/tfs/TB1aX3gsNSYBuNjSspjXXX73VXa-2282-2844.jpg)

![](https://img.alicdn.com/tfs/TB1cwPwsFGWBuNjy0FbXXb4sXXa-2430-3254.jpg)

## Hardware Details

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
