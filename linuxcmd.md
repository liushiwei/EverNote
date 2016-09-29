--- 
title: Linux常用命令
tags: Linux
notebook: linux
---
<!-- MarkdownTOC -->

- [Samba 配置](#samba-配置)

<!-- /MarkdownTOC -->

# Samba 配置
	
	$ sudo service smbd restart
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
    valid users= liusw
    writables = yes
    write list= liusw

```

***********