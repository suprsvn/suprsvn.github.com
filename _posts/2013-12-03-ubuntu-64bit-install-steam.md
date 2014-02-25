---
layout: post
title: 64位ubuntu安装steam错误解决
categories:
- linux
tags:
- linux
- ubuntu
---

> __#suprsvn:__ 一直用的都是ubuntu64位，毕竟i7/8GB内存早已成为标配。 安装steam这个强大的游戏平台时，会出现两个典型的问题。

---

###问题一：

    You are missing the following 32-bit libraries, and Steam may not run: libGL.so.1

###问题二：

    failed to load steamui.so

###解决办法：

    $ sudo apt-get install lib32gcc1
    $ cd ~/.steam/bin
    $ ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1

###OvEr ... :-) ...
