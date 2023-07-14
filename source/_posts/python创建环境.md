
---
title: python创建环境
author: Frank Yu
categories: 
img: https://s2.loli.net/2023/03/11/8nTKz7lUIEvLPSg.png
toc: true
mathjax: true
cover: false
top: false
summary: Some Posts
date: 2023-06-26, Monday
time: 20:05
tags: 
- 
---

什么是venv
Venv（虚拟环境）是Python用来创建和管理虚拟环境的模块，你可以把它想象成一个容器，该容器供你用来存放你的Python脚本以及安装各种Python第三方模块，容器里的环境和本机是完全分开的（就像你在Windows主机上通过Vmware跑一台Ubuntu或者CentOS的虚拟主机一样），也就是说你在venv下通过pip安装的Python第三方模块是不会存在于你本机的环境下的。

为什么使用venv
Python是一个版本更迭很快的程序语言，相应的它所自带的标准库、第三方库甚至pip这个工具也是一样跟着更新频繁，有些模块在更新之后的向下兼容性很差，之前用的上好的脚本在模块升级后就抛出各种异常了。有时你只是为了测试一下更新后的模块而通过pip安装了该模块的新版本，却导致了已经在生产环境中运行的用该模块旧版本写的脚本失效的问题。另外一些模块还是和Python的版本也存在兼容性的问题，Python越学到后面，接触的第三方库和标准库越多，发生这种事情的几率就越大。

为了避免上述问题的发生，我们可以通过venv来为每个项目创建一个虚拟环境，彼此隔离互不打扰，不用担心这次项目所用到的模块的版本、Python的版本会影响到之前写过的脚本，从而为新项目的脚本打造一个更安全、更省心的测试和运行环境。

venv使用方法
通过venv创建的虚拟环境实际是一个文件夹，使用如下命令来创建一个名为py38的虚拟环境：
python -m venv py38
1
python为我们创建了一个名为py38的文件夹，也就是我们的虚拟环境，该目录下包含了Python解释器，标准库和各种支持文件的目录
通过下列命令激活这个虚拟环境，之后我们就正式进入了该虚拟环境（注意命令提示符左边现在出现了(py38)这个代表虚拟环境的文件夹名）。
source py38/bin/activate
1
如果要退出venv，使用命令deactivate即可。
————————————————
版权声明：本文为CSDN博主「githubcurry」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/weixin_45277161/article/details/128940265