# Quick start

This guide offers a glance at AliOS Things, by running directly on a linux machine.  
If you are on Windows or Mac, maybe you'd like to turn directly to our [IDE](https://github.com/alibaba/AliOS-Things/wiki/AliOS-Things-Studio).

## Setup environment

You can either try [Setup Script for Linux/Mac](http://p28phe5s5.bkt.clouddn.com/setup_linux_osx.sh), or manually do steps below,  
e.g. on a Ubuntu 16.04 LTS (Xenial Xerus) 64-bit PC, please make sure pip environment is based on Python 2.7 64bits.

```bash
sudo apt-get install -y python
sudo apt-get install -y python-pip
```
*`Note:`*
1) If meet network issue, you can download python and install it by manually, refer to 'https://tecadmin.net/install-python-2-7-on-ubuntu-and-linuxmint/'
2) For pip install, also download via 'https://mirrors.aliyun.com/pypi/simple/pip/' instead of 'https://pypi.org/project/pip/#files'
then use `python setup.py install` to install pip. 

## Install packages
It is recommended to install `aos-cube` and `relevant packages` globally, which helps developing with AliOS Things Studio in the future.
```bash
# Install aos-cube steps

# Pleae upgrade pip to latest firstly by below command.
$python -m pip install --upgrade pip

$ python -m pip install setuptools
$ python -m pip install wheel
$ python -m pip install aos-cube
```

```bash
# Upgrade aos-cube as below steps

$ python -m pip install --upgrade setuptools
$ python -m pip install --upgrade wheel
$ python -m pip install --upgrade aos-cube
```

*`Note:`* If you meet network issue, you can use below source to install/upgrade pip/aos-cube.
```bash
python -m pip install --trusted-host=mirrors.aliyun.com -i https://mirrors.aliyun.com/pypi/simple/ --upgrade pip
pip install --trusted-host=mirrors.aliyun.com -i https://mirrors.aliyun.com/pypi/simple/   setuptools
pip install --trusted-host=mirrors.aliyun.com -i https://mirrors.aliyun.com/pypi/simple/   wheel
pip install --trusted-host=mirrors.aliyun.com -i https://mirrors.aliyun.com/pypi/simple/   aos-cube

# use doubanio as backup source
pip install  --trusted-host pypi.doubanio.com -i  http://pypi.doubanio.com/simple/  aos-cube
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
