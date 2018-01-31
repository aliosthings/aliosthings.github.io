# Components

AliOS Things provides rich components to support IoT application development.

## 1 Core Components

### 1.1 yloop
yloop is an asynchronous event framework, in charge of dispatching different kinds of events, and managing the scheduling of micro tasks(action).  
With yloop, we can avoid the unexpected complexity or occupancy of resource.  
It supports items below but not limited to:  
- listening of both local and network events
- delayed function calling(callback)
- workqueue, for time-consuming events processing
- APIs for appication, such as register and post events

There will be a main yloop once AliOS Things started. Of course, you can create your own yloops.  
Further more, you can design your own events listening/processing mechanism, as well as messaging routines among components.  

[yloop API](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-API-YLOOP-Guide)

### 1.2 Kernel
kernel is one of the core components of AliOS Things, its predecessor is a RTOS called Rhino.  
The kernel implements a full RTOS fundamentals, including:  
- multitasking
- scheduling
- synchronization, communication, mutex, events
- memory allocation management
- tracing
- multicore processing
- even more...
We can use the APIs provided by kernel to implement a RTOS with rich functionalities.  
Also, it's easy to do a quick porting for new platforms by referring to the porting code of supported CPU architectures.

[Kernel API](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-API-KERNEL-Guide)

### 1.3 Alink
Alink provides the secure cloud service with open and rich resources, including connectivity service, smart network configuration, data reporing, etc.  
With Alink, we can easily build connective application services, like the interaction among users and devices, as well as among devices themselves.  

[Alink API](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-API-ALINK-Guide)

### 1.4 HAL(Hardware Abstract Layer)
HAL is also one of the core components of AliOS Things, targets to adapt the diversity of platforms, chips or architectures,  
so that the application code could be completely portable.  
Now that AliOS Things includes rich implements of HAL, chip vendors or developers can easily access the hardware resources,  
by just implementing corresponding HAL interfaces.  
HAL component supports a variety of hardware interfaces, including adc，flash， gpio，i2c，pwm，rng，rtc，sd，spi，timer，uart，wdg, etc.  
Therefore, we can easily control different hardware perpherals by using HAL APIs.  
Even more, we can refer to these standard APIs provided by HAL, to quickly accomplish new hardware porting.

[HAL API](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-HAL-Porting-Guide)

### 1.5 KV(Key-Value)
KV is a light-weighted persistent storage component, based on key-value pair mechanism.  
It is mainly designed for small footprint devices based on Nor-Flash, provides them common key-value persistent storage interfaces.  
Features:  
- off power protection
- wear leveling
- simple interfaces including set, get, del.

Further more, KV consumes very few resource, with fixed peak RAM usage which only has relationship with max length of key-value pair.  
As for app developers, we can use KV APIs to easily store our product parameters, system configs and so on.

[KV porting](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-HAL-Porting-Guide#22-kv%E7%BB%84%E4%BB%B6%E7%A7%BB%E6%A4%8D%E4%B8%8Eflash-hal%E5%B1%82%E7%9B%B8%E5%85%B3)  
[KV API](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-API-KV-Guide)

### 1.6 VFS(Virtual File System)
VFS is one of the core component of AliOS Things, offers a unified interface to developers for accessing real files and devices.  
It designs an abstract layer for real file system and device operations, provides full portability by implementing a set of unified interfaces to file objects and device objects.  
We can use APIs implemented in VFS, such as `aos_open` `aos_read`, to access file system and devices.  
Therefore, application code can achieve great portability by using VFS, kill the dependencies and couplings of different definitions of the actual file systems.

[VFS API](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-API-VFS-Guide)

### 1.7 uMesh
uMesh is another core component of AliOS Things, makes it possible for hardware modules to form a self-organised network.  
uMesh implements the mesh link management, mesh routing, 6LoWPAN, AES-128, etc.  
It supports raw data packet transportation, as well as IPv4 or IPv6.  
We can programming with sockets, make use of the self-organised network offered by uMesh, to develop the connective applications for smart devices.  
It could be widely used in smart scenarios like lighting, metering, home, etc.  
Similar to other core components, we can just implement the mesh HAL interface, to use uMesh on different transportation solutions, like WiFi, 802.15.4, BLE and so on.

### 1.8 CLI
This is the component `cli` for AliOS Things, just like the shells of \*nix OS.  
We can register or unregister commands to do customization for the command line on demand.  
[CLI API](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-API-CLI-Guide)

It shows an actual command list below:  
![](https://img.alicdn.com/tfs/TB1ETiGdwMPMeJjy1XcXXXpppXa-447-367.png)

### 1.9 uData
uData is a differential core components of AliOS Things.  
The fundamental idea of uData framework comes from the traditional **sensorhub**.  
And this is an IoT oriented sensoring device processing framework integrates both characteristics of actual IoT application scenarios and AliOS Things itself.  
It targets to solve the key problems in IoT devices developing:  
- long development cycle
- short of sensoring application algorithms
- lacking of the ability for connectivity
The original thinking of uData framework follows layered decoupling and modularizing design rules, in order for users to do porting according to their different application scenarios and modularizing requirements.  
It contains two layers:  
- kernel layer: sensor drivers, hardware configuartions and related static calibrations, such as axial calibrations.  
- framework layer: application service management, dynamic calibration management, exported module APIs, etc.

[uData Framework Porting](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-uData-Framework-Porting-Guide)  
[uData Sensor Driver Porting](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-uData-Sensor-Driver-Porting-Guide)

## 2 Feature Components
