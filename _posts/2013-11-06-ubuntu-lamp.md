---
layout: post
title: Ubuntu快速配置LAMP开发环境
categories:
- linux
tags:
- linux
- ubuntu
---

> __#suprsvn:__博客搬到这里后，写博文的欲望又出来，传说中的像黑客一样写文章。最近所有工作全部从Windows迁移到Linux上来了，在配置开发环境，上午抽空又写了一遍[《Vim配置大全》](http://0nly.me/vim/2013/11/06/vim-all.html);傍晚陪女盆友过后就来配置PHP开发环境了，再次写下这篇[《Ubuntu快速配置LAMP开发环境》](http://0nly.me/linux/2013/11/06/ubuntu-lamp.html)，温故知新，方便网友查阅。

---

###1、Ubuntu打开终端输入，一条命令搞定apache+php+MySQL。

    sudo apt-get install apache2 php5 libapache2-mod-php5 mysql-server php5-mysql phpmyadmin

###期间会要求你输入mysql数据库的root用户密码，选择服务器类型［apache］,phpMyAdmin的密码等，按要求出入即可。

---

###2、装完之后重启一下apache，终端输入命令：
    
    sudo /etc/init.d/apache2 restart

---

###3、还要把安装的phpmyadmin链接到/var/www/目录下

__否则http://127.0.0.1/phpmyadmin无法访问，终端命令：__

    cd /var/www/
    sudo ln -s /usr/share/phpmyadmin phpmyadmin

---

###4、默认目录（/var/www/）直接新建文件是没有权限的，为其增加当前用户权限：

    sudo chown username /var/www

__将username替换为您系统当前用户的用户名__

---

###5、局域网终端共享

如果在配置Lamp开发环境的同时，又为了方便家里的各终端（手机/平板）互联的话，而且是双系统的话，例如Win+Ubuntu，可以这样做：

将windows的分区映射到apache服务器下，使局域网中的pad／phone／pc可以访问主机上的文件，实现文件共享与下载：

    sudo ln -s /mnt/00014EB100052901 edisk
    sudo ln -s /mnt/00029D6C000270C2 ddisk

其中`/mnt/**********`为Win分区在Ubuntu挂载的位置。

然后各终端就可以用：

    http://localhost/edisk 或者 http://localhost/ddisk

访问计算机上的资源了，例如下载好的高清电影，歌曲等等。

