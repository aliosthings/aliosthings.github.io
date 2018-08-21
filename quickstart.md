# Quick start

This guide offers a glance at AliOS Things, by running directly on a linux machine.  
If you are on Windows or Mac, maybe you'd like to turn directly to our [IDE](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-Studio).

## Setup environment

You can either try [Setup Script for Linux/Mac](http://p28phe5s5.bkt.clouddn.com/setup_linux_osx.sh), or manually do steps below,  
e.g. on a Ubuntu 16.04 LTS (Xenial Xerus) 64-bit PC

```bash
sudo apt-get install -y python
sudo apt-get install -y gcc-multilib
sudo apt-get install -y libssl-dev libssl-dev:i386
sudo apt-get install -y libncurses5-dev libncurses5-dev:i386
sudo apt-get install -y libreadline-dev libreadline-dev:i386
sudo apt-get install -y python-pip
sudo apt-get install -y minicom

if meet network issue, you can download and install by manually, refer to [How-to-install-python2.7-on-ubuntu](https://tecadmin.net/install-python-2-7-on-ubuntu-and-linuxmint/). 
For pip install, also download via 'https://mirrors.aliyun.com/pypi/simple/pip/' instead of 'https://pypi.org/project/pip/#files'
```

## Install packages
It is recommended to install `aos-cube` and `relevant packages` globally, which helps developing with AliOS Things Studio in the future.
```bash
Pleae upgrade pip to latest firstly by below command.
$python -m pip install --upgrade pip
It is also supported for users to choose which version you prefer, example as below:
$python -m pip install aos-cube==0.2.45


$ python -m pip install setuptools
$ python -m pip install wheel
$ python -m pip install aos-cube
```
**`Note:`** Please make sure pip environment is based on Python 2.7 64bits.

```bash
if you want to upgrade aos-cube, please see below steps:

$ python -m pip install --upgrade setuptools
$ python -m pip install --upgrade wheel
$ python -m pip install --upgrade aos-cube
```
**`Note:`** Please make sure `esptool, pyserial, scons` and `aos-cube` are installed sucessfully when run `pip install aos-cube`, or you can install them one by one if you meet problems.

**`Note:`** If you meet network issue, you can use below source to install/upgrade pip/aos-cube.
```bash
python -m pip install --trusted-host=mirrors.aliyun.com -i https://mirrors.aliyun.com/pypi/simple/ --upgrade pip
pip install --trusted-host=mirrors.aliyun.com -i https://mirrors.aliyun.com/pypi/simple/   setuptools
pip install --trusted-host=mirrors.aliyun.com -i https://mirrors.aliyun.com/pypi/simple/   wheel
pip install --trusted-host=mirrors.aliyun.com -i https://mirrors.aliyun.com/pypi/simple/   aos-cube
pip install  --trusted-host pypi.doubanio.com -i  http://pypi.doubanio.com/simple/  aos-cube==0.2.50

```

## Run

```bash
git clone https://github.com/alibaba/AliOS-Things.git
cd AliOS-Things
aos make helloworld@linuxhost
./out/helloworld@linuxhost/binary/helloworld@linuxhost.elf
```

Note: Please use below domestic git source if you meet network issue
```bash
 git clone https://gitee.com/alios-things/AliOS-Things.git
```


## Result

There you can see the delayed action starts in 1 sec and getting triggered every 5 secs.
```bash
$ ./out/helloworld@linuxhost/binary/helloworld@linuxhost.elf
 [   1.000]<V> AOS [app_delayed_action#9] : app_delayed_action:9 app
 [   6.000]<V> AOS [app_delayed_action#9] : app_delayed_action:9 app
 [  11.000]<V> AOS [app_delayed_action#9] : app_delayed_action:9 app
 [  16.000]<V> AOS [app_delayed_action#9] : app_delayed_action:9 app
 ```
