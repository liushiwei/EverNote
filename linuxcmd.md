--- 
title: Linux常用命令
tags: Linux
notebook: linux
---
<!-- MarkdownTOC -->

- [Samba 配置](#samba-配置)
- [ubuntu system setup](#ubuntu-system-setup)

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