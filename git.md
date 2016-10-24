--- 
title: Git常用方法
tags: Git
notebook: George 的笔记本
---

<!-- MarkdownTOC -->

- [git查看某个文件的修改历史](#git查看某个文件的修改历史)
- [git加入忽略文件权限的配置](#git加入忽略文件权限的配置)
- [git配置别名](#git配置别名)

<!-- /MarkdownTOC -->


# git查看某个文件的修改历史

```shell
	git log --pretty=oneline 文件名
```

# git加入忽略文件权限的配置

```shell

	git config core.filemode false

``` 

# git配置别名

```shell

	git config --global alias.st status
	git config --global alias.co checkout
	git config --global alias.ci commit
	git config --global alias.br branch
	git config --global alias.unstage 'reset HEAD -i'
	git config --global alias.last 'log -1'
	git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

```
	配置文件

	配置Git的时候，加上--global是针对当前用户起作用的，如果不加，那只针对当前的仓库起作用。

	配置文件放哪了？每个仓库的Git配置文件都放在.git/config文件中：

	别名就在[alias]后面，要删除别名，直接把对应的行删掉即可。

	而当前用户的Git配置文件放在用户主目录下的一个隐藏文件.gitconfig中：