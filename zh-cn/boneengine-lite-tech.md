# BoneEngine@Lite

**关键词说明** ：

TinyEngine： BoneEngine@Lite的别名用语，等同于BoneEngine@Lite。



## BoneEngine@Lite背景介绍

BoneEngine@Lite是一个专门为嵌入式系统设计且面向IOT业务的高性能JavaScript引擎，同时针对主流的嵌入式操作系统提供一体化的开发框架，提供丰富的扩展接口及调试手段，以方便开发者开发。

通过BoneEngine@Lite引擎，之前在物联网领域必须通过C/C++来开发的方式也可以通过javascript语言来开发了。C/C++语言更倾向于内核及硬件底层的开发，而javascript语言更适合在内核之上开发物联网应用。

不同于Node.js，BoneEngine@Lite更加轻量化，适用于资源（CPU/ROM/RAM) 比较紧张的场景，当前主流的轻量化js引擎有Tiny-JS, JerryScript, Espruino, Duktape等。

BoneEngine@Lite的主要特点有:

- 面向IOT业务的高性能JS引擎

  - 资源占用少，BoneEngine@Lite专门针对嵌入式系统设计，所以在jse部分做了性能优化和裁剪。经测试，可以做到在RAM<10KB,ROM<10KB的系统上运行。
  - CPU性能高，通过优化的词法和句法分析器，支持栈模式，降低了CPU的使用率。
  - 面向IOT应用场景的JS支持能力，由于BoneEngine是面向IoT的，所以其内置了面向IOT的ES精简语法及常用的IOT功能模块，如MQTT，WIFI，HARDWARE扩展等。

- 跨平台及一体化的应用编程框架

  - 通过硬件抽象层HAL，及操作系统抽象层OSAL，BoneEngine@Lite可以运行在aos，freertos，linux之上。
  - 在OSAL和HAL层之上，BoneEngine@Lite构建了统一的物联网应用开发框架，内置了设备上云的能力，与阿里云一站式开发平台可以直接对接，并有标准的设备模型。
  - 支持板级驱动，模块，设备驱动 的动态加载，js应用可以云端动态加载运行。

- 提供一体化开源部署工具

  - BoneEngine@Lite提供了基于IDE图形化和CLI命令行的开发和部署工具，方便开发者方便的基于BoneEngine@Lite来开发IOT应用。

- 开源的开发者生态

  - BoneEngine@Lite通过开源吸引更过的开发者和ISV使用，并基于不同的IOT场景开发出更多的IOT应用。逐步完善基于阿里IOT的开源生态。

    ​

## 为什么要开发BoneEngine@Lite

上面介绍了BoneEngine@Lite的这些优点，那么下一步我们来讲讲为什么要开发BoneEngine@Lite以及BoneEngine@Lite技术解决当前的什么实际问题。

### 物联网设备的开发现状及问题

时下物联网开发比较火热，但是也暴露出物联网开发的一些问题。传统的物联网开发属于嵌入式开发，要求开发者具备较强的C/C++语言知识，同时要有较强的硬件基础，如通过指针操作内存，通过系统调用操作外设，通过寄存器读取外设状态等等。这对于开发者提出了较高的编程语言能力要求。同时传统的物联网开发由于使用本地编译，链接，下载的方式，针对不同的设备或平台，即使是完成同样的应用场景，例如点灯这个操作，也需要重新编译，链接下载，这种方式在物联网终端分散，碎片化，场景应用复杂的需求下，这种开发方式显得有些效率低下。另外由于C/C++的调试方式以gdb为主，图形化的调试工具较少或性能较低，也给后期的调试，发布带来了一些困难。

总的来说，当前的物联网开发现状如下：

- 开发难度高，需要有硬件基础。
- 模块复用难，集成功能效率低下。
- 开发和调试手段较少。
- 发布及升级有风险。

### BoneEngine@Lite是如何解决这些问题的

前面提到了传统的物联网设备开发的一些局限性，那么BoneEngine@Lite是如何解决这些问题的？

其关键在于引入了解释型语言JavaScript，解释型语言是相对于编译型语言来说的，解释型语言是指使用专门的解释器对源程序进行逐行解释成特定平台的机器码并立即执行的语言。由于有了解释器，所以语言无需提前编译，可以直接在运行的时候解析并运行。所以BoneEngine@Lite通过在嵌入式系统上实现javascript的解析器，使得javascript也可以运行在嵌入式系统甚至没有os的单片机上。

其次BoneEngine@Lite通过抽象操作系统接口层OSAL及硬件抽象层HAL，使得其可以运行在不同的系统和硬件上面，屏蔽了os和硬件的细节，使得开发者可以专心于使用javascript来开发应用。

最后，BoneEngine@Lite通过针对IOT开发的framework，提供了常用的IOT协议，如http，mqtt，wifi，zigbee等。并直接对接阿里一站式开发平台，使得开发一款IOT设备更加简单。



### 为什么选择javascrpit作为BoneEngine@Lite的应用层开发语言

前面提到了解释型语言是BoneEngine@Lite解决传统嵌入式开发问题的关键，那么解释型语言有lua，python，perl等，为什么要选择javascript呢？

这里有几点原因，javascript是时下比较流行的web开发语言，拥有众多的开发者，这部分开发者可以在无门槛的情况下来开发物联网应用，这对于IOT生态是非常有利的。另外javascript语言有很多开源的开发框架，可以更加方便的开发应用。其次是javascript语言本身是高效、简单、易用的，其性能可以接近C，但是相比C更加容易使用和适合业务开发。最后是javascript的IDE、调试手段比较丰富，如断点，内存分析，在线调试等。



## BoneEngine@Lite系统框图

![image | left](https://gw.alicdn.com/tfs/TB1OfxbxqmWBuNjy1XaXXXCbXXa-2812-1529.png)



### 芯片及硬件

BoneEngine@Lite 可支持多种不同架构的Soc,CPU,MCU:

- 芯片模组：
  - 乐鑫ESP32，ESP8266，
  - 庆科EMW3060，EMW3080，
  - STMicroelectronics的STM32xx等模组芯片；
- 可以运行在IA32/IA64 PC上，用于调试或开发的仿真器；
- 也可以运行在边缘 Linux 网关（MIPS），树莓派（ARM）等资源丰富的设备上。

### 内核及驱动

BoneEngine@Lite 可以运行在AliOS-Things系统之上:

BoneEngine@Lite 还提供虚拟设备，可运行在Windows，Linux，MacOS等Host主机上，做为调试器使用。



### 系统及硬件抽象层

BoneEngine@Lite 为支持跨平台，跨OS系统能力，针对不同OS，Soc芯片和硬件，统一封装抽象接口，这样客户在应用或产品切换到不同平台时，上层应用不用替换，从而可以保证快速移植和产品化，也能达到“一份代码，处处运行”的目标。

OSAL（系统抽象层）将 BoneEngine 所需的与操作系统的相关函数进行封装。 目前 BoneEngine 主要需要内核提供任务调度，定时器，进程间通讯等基本功能，由于AOS和其他RTOS函数接口不一致，因此系统抽象层将完成操作系统函数的统一。

硬件抽象层则统一不同平台的硬件驱动接口。针对不同平台提供的外部硬件接口，对接硬件接口或者驱动实现统一封装，供BoneEngine@Lite的Native eXtension Modules 如 HW 模块调用。 目前Gravity支持的硬件模块包括:

- GPIO
- I2C
- I2S
- ADC
- PWM
- UART
- SPI
- Board
- WIFI
- Bluetooth
- Flash



## BoneEngine@Lite 应用编程框架

应用编程框架是 BoneEngine@Lite 最主要部分，既包括JS应用的运行环境，也包含了大量的扩展模块，扩展模块通过API的方式暴露给JS应用开发者调用。框架的目的在于：一方面隔离应用对底层硬件和操作系统的依赖，一方面封装大量的扩展接口，方便让开发者在JS层调用，另外，扩展模块由Native C实现，可以提高性能，整个框架包括 :

- Javascript 引擎（BoneEngine@Lite）
- 硬件内置扩展模块： GPIO，I2S，I2C，ADC，PWM，SPI，WIFI，Flash
- IoT相关服务，组件的本地扩展模块： 如 MQTT，HTTP，CoAP
- 服务
  - AppManager 应用管理
  - BoardManager 板级配置管理
  - debugger 设备调试
- 应用组件
  - 标准设备模型：阿里标准设备模型，包括设备三要素（属性，事件，方法）
  - 硬件驱动代理：应用程调用硬件驱动的代理，
  - Cloud-client ：通过MQTT和阿里 Link Platform 平台连接

## OS 抽象及硬件设备抽象

![image | left](https://gw.alicdn.com/tfs/TB1u3ZtxhGYBuNjy0FnXXX5lpXa-1364-855.png)

OSAL 与硬件抽象层的目的是：

- 隔离 BoneEngine@Lite 与底层 OS 系统的依赖，便于跨OS移植
- 隔离 BoneEngine@Lite 与底层硬件平台依赖，便于跨芯片移植

OS抽象层设计原则：

- 根据目前 AOS 已提供的API封装BoneEngine需要的OSAL接口
- 其他 OS( FreeRTOS,Linux,MacOS)，统一按照以上定义接口实现和封装

硬件抽象层设计原则：

- AOS 已经提供了HAL层，BoneEngine直接和验证使用该接口
- 其他 OS( FreeRTOS,Linux,MacOS)按照以上接口实现和封装

数据接口定义：

- 任务(task)：create,destroy，delay

- 事件（event)：post,register

- 定时器（timer) post,register

- 硬件 IO： \* GPIO：init/deinit,ouput\_high/low,input\_get,enable/disable\_irq \* UART：init/deinit,send,recv \* ADC：init/deinit,get \* I2C：init/deinit,master\_send/recv, slave\_send/recv, mem\_send/recv \* SPI：init/deinit,send,recv,send\_recv \* Timer：init/deinit,start,stop \* FLASH：get\_info,erase,erase\_write,read,secure,desecure

  
## 应用管理 AppManager 

AppManager管理应用的安装，下载，运行.

![image | left](https://gw.alicdn.com/tfs/TB1BwXbxqmWBuNjy1XaXXXCbXXa-1383-1037.png)

在 BoneEngine@Lite 中，为了便于JS应用程序的安全存储，分发和管理，对应用程序打成APP-PACK，该包中，包含了文件应用程序的文件列表，版本，包签名证书等信息。在云端和本地开发环境包含了打包和拆包工具，可以把整个JS程序，board-cfg.json配置文件以及其他库文件打包成整个应用包。

例如：一个普通Gravity应用程序可以如下几个文件组成：

```
    .
├── drivers
│   ├── door.js
│   ├── fan.js
│   ├── light.js
│   └── temp.js
├── index.js
├── device.js
├── README.md
└── version.js
```

具体说明：

```
index.js
   JS应用程序执行入口
device.js
   设备上云相关操作类
version.js
   JS应用程序版本信息模块文件
drivers
   JS应用需要使用到的设备对象模块，与具体硬件相关，操作buildin的hw对象
```



## 板级配置管理 BoardManager

板级配置管理服务主要负责：

- 动态配置板级的管脚，端口映射
- 生成 BoneEngine 的静态HW全局JS对象
- 管理板级硬件资源初始化，资源分配以及释放

![image | left](https://gw.alicdn.com/tfs/TB1YMlbxqmWBuNjy1XaXXXCbXXa-1428-906.png)

典型板级配置 board\_config.json 文件如下：

```
{
    /*串口配置*/
    "UART":[
        {
        "id":"uart1",
        "port":1,
        "data_width":3,
        "baud_rate":115200,
        "stop_bits":0,
        "flow_control":0,
        "parity_config":0
        },
        {
        "id":"uart2",
        "port":2,
        "data_width":3,
        "baud_rate":115200,
        "stop_bits":0,
        "flow_control":0,
        "parity_config":0
        }
    ]
}
```

board\_config.json 配置文件可以和APP-PACK一起下发，也可以在出厂时直接烧写，如果系统没有该配置文件，使用缺省映射。



## Javascript Engine for BoneEngine@Lite

Javascript Engine 专门为资源有限的设备提供的轻量级的 Javascript 引擎，相对于V8，SpideMonkey 功能强大的JS引擎，BoneEngine@Lite 不支持JIT功能，但是对JS语法集支持做了精简，而针对IoT特定需求，对硬件驱动，操作系统函数，以及MQTT，MESH等功能模块实现了JS语法扩展，开发者可以直接通过JS API调用这些功能模块

BoneEngine@Lite 具有如下特点：

- 资源占用：RAM<15KB,ROM(Footprint) <15KB

- CPU性能：优化的词法和句法分析器，降低CPU使用率

- JS 支持能力：面向IOT的 ES 精简语法 ，CommonJS 支持，IoT 内置模块

  