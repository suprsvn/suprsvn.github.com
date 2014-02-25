---
layout: post
title: virtualenv环境下安装MySQL-python报错
categories:
- python
tags:
- django
---

> __#suprsvn:__ 今天在windows重新配置了django开发环境后，需要链接MySQL数据库，这就需要安装MySQL-python这个组件。

---

###错误原因（有图）：

> 如果是在python的虚拟环境virtualenv下安装的话，直接`pip install MySQL-python`会出现以下error：

    error: Unable to find vcvarsall.bat

分析一下原因，是由于没有安装visual studio 2010 的原因，也就是没有C语言的编译环境。

![错误图](http://suprsvn.qiniudn.com/codelog/virtualenv-mysql-python-error.png)

###解决办法：

1、先将virtualenv添加进环境变量；

2、命令行输入`activate`进入python的虚拟环境；

3、然后直接easy_install下载好的适用于windows的MySQL-python，即可安装成功。

    easy_install MySQL-python-1.2.4.win32-py2.7.exe

4、适用于windows的MySQL-python的下载地址：[MySQL-python(win32)](http://www.lfd.uci.edu/~gohlke/pythonlibs/#mysql-python)

---

### OvEr … :-) …

---
