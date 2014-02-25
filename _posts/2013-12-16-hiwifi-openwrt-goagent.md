---
layout: post
title: HiWifi刷openwrt加入goagent
categories:
- linux
tags:
- tools
---

> __#suprsvn:__ 在入手极路由HiWifi之前的很长一段时间都在了解openwrt配置openvpn来翻蔷，正好遇到HiWifi大酬宾99元“大甩卖”，就入了。关键是看中它可以刷openwrt。昨天试了一下配置openv，结果没有成功，然后想到既然openwrt是linux，肯定能用python吧，那很简单就可以直接将Goagent给加进去，然后设置路由器开机启动项，不就ok了。思路来了，就行动。看步骤

---

###一、首先去openwrt确认路由器能刷openwrt，这是一切的前提。刷机的方法大同小异，HiWifi的是这样：（不同的路由器刷机方法自行Google啊）

1、PC的地址设置为：
    ip地址：192.168.1.88
    子网掩码:255.255.255.0

2、确保openwrt固件已重命名为recovery.bin，并放于tftp32.exe根目录；打开tftp32.exe工具，

3、断开路由器电源，网线链接PC与路由器Lan口，尖锐物顶住路由器RST键*不放*，给路由加电。

4、这时tftp32开始上传固件到路由器，出现进度条，待进度条完成并自动消失后，松开RST键。

5、路由器进入跑马灯状态，大约需3~5分钟会重启，重启后已刷好；可以`ping 192.168.1.1`，通了说明路由器启动成功。

6、浏览器进入路由器后台`192.168.1.1`，首次进入请先设置密码。

7、准备工作就是设置好PPPoE拨号，设置wifi热点，设置语言为简体中文等等，自己摸索吧，毕竟以后都要跟openwrt打交道。

---

###二、开始在路由器中布置goagent。

1、获取最新版的Goagent（3.1.0），需要上传的文件为：

    certs文件夹、CA.crt、cacert.pem、proxy.ini、proxy.py、proxy.pac

2、修改proxy.ini，只修改两行行，[listen]中的ip改为`ip = 0.0.0.0`,[gae]中的appid改为你自己的。

3、修改proxy.pac，批量替换`127.0.0.1`为`192.168.1.1`。

4、将certs文件夹、CA.crt、cacert.pem、proxy.ini、proxy.py（1中的前5个）文件放到一个文件夹中，例如goagent/。

5、下载putty，放入WinSCP根目录，用`WinSCP`链接路由器，地址为192.168.1.1，用户名为root，密码为设置的后台密码。
按图示打开putty,输入路由器后台密码。

![WinScp_Putty](http://0nly.me/images/winscp-putty.png)

6、已进入openwrt终端了，安装一些依赖。

{% highlight python %}

opkg update
opkg install openssl
opkg install python
opkg install pyopenssl python-openssl
opkg install python-greenlet
opkg install gevent

{% endhighlight %}

7、安装完成后，退出Putty，用WinSCP将准备好的goagent目录放入路由器根目录下，将proxy.pac放入www、目录下。如图：

![Goagent_Dir](http://0nly.me/images/winscp-goagent-dir.png)
![Goagent_Wwww](http://0nly.me/images/winscp-goagent-www.png)

8、将Goagent加入路由器openwrt的启动项中，添加完毕后，记得*提交*。如图：

![openwrt_menu](http://0nly.me/images/openwrt-startup-menu.png)
![openwrt_goagent](http://0nly.me/images/openwrt-startip-goagent.png)

9、重启路由器，由于加入了python，还运行了goagent，启动会稍微慢一点。

10、将IE的代理设置为http://192.168.1.1/proxy.pac。现在明白为什么把proxy.pac放入www目录了吧。

11、也可使用其它浏览器啊，Chrome+switchysharp，firefox+autoproxy，这些是黄金组合。

12、家里其他各终端再也不用个个都安装插件/app了，链接wifi的时候直接填写代理，并导入goagent的`CA.crt`即可，如图：

![android_proxy](http://0nly.me/images/android-wifi-proxy.png)

---

### OvEr … :-) …

---
