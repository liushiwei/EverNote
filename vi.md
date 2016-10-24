--- 
title: VI常用命令
tags: Linux
notebook: linux
---
<!-- MarkdownTOC -->

- [两种方法可以可以实现临时退出 Vi/Vim、进入 shell 环境后再回来的要求](#两种方法可以可以实现临时退出-vivim、进入-shell-环境后再回来的要求)

<!-- /MarkdownTOC -->

# 两种方法可以可以实现临时退出 Vi/Vim、进入 shell 环境后再回来的要求

方法一：使用 Ctrl-z 以及 fg 这两个命令组合。

　　这一解决方法主要利用了 Linux/Unix 的作业机制。具体原理是：Ctrl-z 命令将当前的 Vi/Vim 进程放到后台执行，之后 shell 环境即可为你所用；fg 命令则将位于后台的 Vi/Vim 进程放到前台执行，这样我们就再次进入 Vi/Vim 操作界面并恢复到原先的编辑状态。

方法二：使用行命令 :sh。

　　在 Vi/Vim 的正常模式下输入 :sh即可进入 Linux/Unix shell 环境。在要返回到 Vi/Vim 编辑环境时，输入 exit 命令即可。

　　这两种方法实现机制不一定，但效果一样，都非常快捷有效。