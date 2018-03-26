# AliOS Things Starter Kit

AliOS Things Starter Kit provides rich resources，including on-board sensors, LCD screen(240*240), audio, WiFi module, etc.
Even more, it is insanely easy for user to develop applications and extensions, thanks to AliOS Things, this powerful, flexible RTOS with all kinds of components.

As for developing and debugging, Starter Kit has integrated ST-LINK V2, no need for any external debugger.

To simplify the development of Starter Kit, AliOS Studio IDE is offered to users for the one stop developing experience, including building, firmware uploading and debugging.


## Features

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

## Snapshot

![](https://img.alicdn.com/tfs/TB14PI2gDtYBeNjy1XdXXXXyVXa-922-945.png)

## Hardware Details

| **Item**                      | **Description**                                              | **Specification**                                                     |
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

## GUI Demo

![](https://img.alicdn.com/tfs/TB17EnugqmWBuNjy1XaXXXCbXXa-484-387.gif)

Learn more here:  
[Play Starter Kit with AliOS Studio](https://github.com/alibaba/AliOS-Things/wiki/starterkit-tutorial)
