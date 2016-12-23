--- 
title: Linux常用命令
tags: Linux
notebook: linux
---
<!-- MarkdownTOC -->

- [Samba 配置](#samba-配置)
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