---
layout: post
title: kubuntu安装爱壁纸HD
categories:
- linux
tags:
- linux
- ubuntu
---

> __#suprsvn:__ 原生ubuntu下方便的换壁纸程序就是ubuntu tweak中内置的爱壁纸HD了，而我一直使用的是KDE，在KDE下安装GTK界面的tweak实在是难受。在爱壁纸HD官网上看到了KDE安装它的方法，并且是Qt界面的;试了一下，很好看很实用，比tweak中内置的爱壁纸HD选出来的壁纸好多了。

---

##有图有真相：

![爱壁纸HD](http://suprsvn.qiniudn.com/codelog/lovewallpapers1.png)

![爱壁纸HD](http://suprsvn.qiniudn.com/codelog/lovewallpapers2.png)

---

###终端apt-get直接就可以搞定依赖关系：

    sudo apt-get install xdotool python-pyside python-support

###爱壁纸官网下载deb包，之后终端安装：

    sudo dpkg -i LoveWallpaper4Linux.deb

###如果未满足依赖关系就：

    sudo apt-get -f install

###OvEr ... :-) ...
