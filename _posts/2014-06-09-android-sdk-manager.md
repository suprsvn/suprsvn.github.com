---
layout: post
title: Android SDK Manager速度太慢的解决办法
categories:
- android
---

这两天在TC里面Google的各种服务是根本不能用。昨天又从Win直接转移到Ubuntu，需要重新下载SDK的各种文件，各种API，但是无论是挂着goagent还是VPN，Android SDK Manager就是无速度。突然想到，修改hosts文件这种简单有内涵的方法，没想到收获甚佳，不仅秒fetch，而且下载速度可以撑满带宽。

---

我是在Ubuntu下，修改hosts文件后直接生效，考虑到平时用Google来提高效率，于是我将下面链接的hosts内容全部append到`/etc/hosts`中了。

[hosts文件的开源链接](https://raw.githubusercontent.com/smarthosts/SmartHosts/master/trunk/hosts)

若你平时不用Google，只是SDK下载，那就只需将以下两项加入`/etc/hosts` 中即可。

{% highlight python %}
203.208.46.200	dl-ssl.google.com
203.208.46.200	www.google.com
{% endhighlight %}

这里还有我备份的hosts文件，如果上面链接打不开，可以下载这个。 

[备份hosts下载](http://0nly.me/contents/hosts)

---

### OvEr … :-) …

---
