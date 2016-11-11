---
title: install mysql macos x
date: 2016-11-11 16:29:14
tags:
- MacOs
categories:
- IT
---
MacOS安装配置Mysql<!--more-->

> 安装映像中的两个安装包文件。
[pkg下载链接请点击](http://dev.mysql.com/doc/refman/5.6/en/osx-installation-pkg.html)
a. mysql-5.1.44-osx10.6-x86_64.pkg（mysql标准版安装）
b. MySQLStartupItem.pkg（mysql启动项目），可以在你电脑启动系统时自动运行mysql服务，它安装在/Library /StartupItems/MySQL/，如果你不想系统启动时运行mysql服务，请不要安装。如果你在安装后又不想使用，请删除/Library /StartupItems/MySQL/这个目录。
3 启动mysql服务
1、如果你已经安装了MySQLStartupItem.pkg，重新启动电脑即可。
2、如果你有安装MySQLStartupItem.pkg或者不想启动电脑，运行：应用程序－实用工具－终端，在终端中输入命令：sudo /Library/StartupItems/MySQLCOM/MySQLCOM start，然后输入你的系统管理员密码即可。
4 关闭mysql服务
终端中输入命令：sudo /Library/StartupItems/MySQLCOM/MySQLCOM stop，然后输入你的系统管理员密码即可。
你也可以去系统偏好设置－其他－MySQL，通过这个来启动和停止MySQL服务。
5 更改mysql root账户密码
终端中输入命令：/usr/local/mysql/bin/mysqladmin -u root password 新密码
你可以随时使用这条命令更改你的密码。
6 终端登录mysql
终端中输入命令：/usr/local/mysql/bin/mysql即可。

----------
> Preference Pane启动（专为客户端）
MySQLStartupItem.pkg（mysql启动项目）是专为开机启动准备的，如果没有安装，那么使用系统偏好设置，搜索mysql启动即可

----------
> 修改密码，登录数据库（终端)
[实用博客链接请点击](http://blog.csdn.net/u014410695/article/details/50630233)
启动指令：/usr/local/mysql/bin/mysql -u root -p