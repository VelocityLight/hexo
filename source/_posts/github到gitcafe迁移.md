---
title: github到gitcafe迁移
date: 2016-11-13 11:09:22
tags:
- gitcafe迁移
categories:
- IT
---
众所周知Github于国内连接是非常缓慢的，国内建站以及代码管理有一个gitcafe，前一段时间纳入了coding.net，是一个很好的平台。在此记录在mac下，将hexo博客从github到gitcafe的迁移<!--more-->

首先登陆[coding.net][1]注册账号,可以参考[建立公钥官方链接][2]，若需要建立专属于gitcafe的SSH key，则如下操作（为了防止覆盖）

> **[建立专属于gitcafe的SSH key][3]**
1). 进入 SSH 目录
cd ~/.ssh
#如果还没有 ~/.ssh 目录的话，请先手工创建一个 mkdir ~/.ssh 。
2). 生成新的 SSH 秘钥 (记得把以下命令中的 your_email@youremail.com 改为你的 Email 地址 )
ssh-keygen -t rsa -C "your_email@youremail.com" -f ~/.ssh/gitcafe
3). 生成过程中会出现以下信息，按屏幕提示操作，并记得输入 passphrase 口令。(笔者一般在此是直接回车不输入密码的)
$ ssh-keygen -t rsa -C "your_email@youremail.com" -f ~/.ssh/gitcafe
```
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/username/.ssh/gitcafe.
Your public key has been saved in /c/Users/username/.ssh/gitcafe.pub.
The key fingerprint is:
15:81:d2:7a:c6:6c:0f:ec:b0:b6:d4:18:b8:d1:41:48 your_email@youremail.com
```
4). SSH 秘钥生成结束后，你可以在用户目录 (~/.ssh/) 下看到私钥 gitcafe 和公钥 gitcafe.pub 这两个文件，记住千万不要把私钥文件gitcafe 透露给任何人。
5). 在 SSH 用户配置文件 ~/.ssh/config 中指定证书名称，如果没有 config 文件的话就新建一个 (Linux 平台的话需使用该命令chmod 644 ~/.ssh/config 来改变 config 文件权限)，并输入以下内容：
```
Host git.coding.net
User your_email@youremail.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/gitcafe
```
另：Port 443为http端口号，Port 22为SSH端口号，可以通过这个进行指定。一般不填默认使用SSH。

--------
> **[双线部署，选择coding.pages][4]**
额外参考：[双线部署姊妹篇][5]
[官方双线部署文档][6]

--------
> Hexo deploy
```
deploy:
  type: git
  repository: 
  	coding: git@git.coding.net:VelocityLight/VelocityLight.git,coding-pages
```
注：coding-pages表示部署到coding-pages分支；repository下添加github地址可同时deploy

[1]:https://coding.net/user
[2]:https://coding.net/help/doc/git/ssh-key.html
[3]:http://blog.csdn.net/ichsonx/article/details/8625925
[4]:http://www.ieclipse.cn/2016/09/08/Web/hexo-coding-pages/
[5]:http://www.ieclipse.cn/2016/08/29/Web/Hexo-deploy-lines/
[6]:https://coding.net/help/doc/pages/index.html
