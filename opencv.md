--- 
title: Opencv3.0
tags: Linux Opencv Ubuntu
notebook: linux
---

<!-- MarkdownTOC -->

- [Opencv Install](#opencv-install)
- [ccgo intall](#ccgo-intall)

<!-- /MarkdownTOC -->


# Opencv Install 

```shell

[compiler] sudo apt-get install build-essential
[required] sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
[optional] sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev

cd ~/opencv-3.0.0-rc1
mkdir release
cd release
cp ippicv_linux_20151201.tgz opencv-3.1.0/3rdparty/ippicv/downloads/linux-808b791a6eac9ed78d32a7666804320e
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..
make
sudo make install

```

# ccgo intall

```shell
wget http://ccdw.org/~cjj/prog/ccgo/src/ccgo-0.3.6.5.tar.gz
tar -zxvf ccgo-0.3.6.5.tar.gz
cd ccgo-0.3.6.5
 sudo apt-get install libgconfmm-2.6-dev
sudo apt-get install libncurses-dev
./configure

