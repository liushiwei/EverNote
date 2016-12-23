--- 
title: Linux常用命令
tags: Linux
notebook: linux
---
<!-- MarkdownTOC -->

- [Samba 配置](#samba-配置)
- [adb shell 没有权限的问题](#adb-shell-没有权限的问题)
- [ubuntu system setup](#ubuntu-system-setup)
- [ubuntu samba mount](#ubuntu-samba-mount)
- [find cmd](#find-cmd)
- [列出某个IP地址所提供的共享文件夹](#列出某个ip地址所提供的共享文件夹)

<!-- /MarkdownTOC -->

# Samba 配置
	
    $ sudo service smbd restart
    $ sudo apt-get install samba
    $ sudo smbpasswd -a george
    $ sudo vim /etc/samba/smb.conf

```shell

[liusw]
    comment = Private Directory
    path = /home1/liusw
    valid users= liusw
    writables = yes
    write list= liusw


[tansf]
    comment = Private Directory
    path = /home/tansf
    writables = yes


[huangjh]
    comment = Private Directory
    path = /home/huangjh
    writables = yes

[home]
    comment = Private Directory
    path = /home/
    valid users= george
    writables = yes
    write list= george

```

***********

# adb shell 没有权限的问题

If I run lsusb, I can see which devices I have connected, and where:

```shell
$ lsusb
...
Bus 002 Device 050: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone ...
Bus 002 Device 049: ID 18d1:4e42 Google Inc. 

```

This is showing my Samsung Galaxy S3 and my Nexus 7 (2012) connected.

Checking the permissions on those:

```shell

$ ls -l /dev/bus/usb/002/{049,050}
crw-rw-r--  1 root root    189, 176 Oct 10 10:09 /dev/bus/usb/002/049
crw-rw-r--+ 1 root plugdev 189, 177 Oct 10 10:12 /dev/bus/usb/002/050

```

Wait. What? Where did that "plugdev" group come from?

```shell

$ cd /lib/udev/rules.d/
$ grep -R "6860.*plugdev" .
./40-libgphoto2-2.rules:ATTRS{idVendor}=="0bb4", ATTRS{idProduct}=="6860", \
  ENV{ID_GPHOTO2}="1", ENV{GPHOTO2_DRIVER}="proprietary", \
  ENV{ID_MEDIA_PLAYER}="1", MODE="0664", GROUP="plugdev"
./40-libgphoto2-2.rules:ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="6860", \
  ENV{ID_GPHOTO2}="1", ENV{GPHOTO2_DRIVER}="proprietary", \
  ENV{ID_MEDIA_PLAYER}="1", MODE="0664", GROUP="plugdev"

```

Add a rule

Create a file /etc/udev/rules.d/99-adb.rules containing the following line:

```shell
ATTRS{idVendor}=="18d1", ATTRS{idProduct}=="4e42", ENV{ID_GPHOTO2}="1",
  ENV{GPHOTO2_DRIVER}="proprietary", ENV{ID_MEDIA_PLAYER}="1",
  MODE="0664", GROUP="plugdev"bndxgae
```

# ubuntu system setup

```shell

sudo apt-get install gnome-control-center
sudo apt-get install ubuntu-desktop

```


# ubuntu samba mount

```shell

sudo apt-get install cifs-utils
 sudo mount.cifs  //192.168.0.32/home /home/george/servers32 -o user=liusw pass=liusw
 
```

# find cmd

```shell

find . -type f -regex ".*/[0-9a-z_]+" -exec chmod u+x {} \;

```

# 列出某个IP地址所提供的共享文件夹

```shell

smbclient -L 198.168.0.1 -U username%password

```