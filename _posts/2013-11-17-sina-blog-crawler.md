---
layout: post
title: 新浪博客博文爬虫
categories:
- python
---

最近有需要爬取新浪博客博文，写了这个python小爬虫。

---

### 复制下面代码，保存为crawler.py,并在同目录下创建articles文件夹即可。
### http://blog.sina.com.cn/s/articlelist_1191258123_0_1.html可用韩寒博文目录试验一下。博文目录页数，想抓几页就输入几页。


{% highlight python %}

#!/usr/bin/python
# -*- coding: utf-8 -*-

import urllib
import os
import sys

#打开博客首页,点击"博文目录",得到博文目录Url
listUrl = raw_input('[请输入博文目录Url: ]')
pages = raw_input('[请输入要抓取的博文目录页数:]')

#抓取的文章默认存放目录,可手动创建并修改.
path = r'articles'

def mkdir(path):
    isExists=os.path.exists(path)
    if not isExists:
        print path+'[目录不存在,请手动创建后再次运行此脚本!]'
        sys.exit()
    else:
        pass

def saveLog(blogUrl):
    if blogUrl != '':
        content = urllib.urlopen(blogUrl).read()
        mkdir(path)
        open((r'%s/') % path + blogUrl[-26:], 'w+').write(content)
        print 'Article [ ', blogUrl, ' ] is saved.'
    else:
        print '... OvEr ...:-)...'

for j in range(1, int(pages)+1):
    blogUrl = ['']
    listHead = listUrl[0:(listUrl.find(listUrl[-6:]))]
    listUrlFull = listHead + str(j) + listUrl[-5:]
    print '开始下载页面['+str(j)+']中的文章 ...'
    page = urllib.urlopen(listUrlFull)
    con = page.read()

    title = con.find(r'<a title=', 0)
    href = con.find(r'href=', title)
    html = con.find(r'.html', href)
    blogUrl = con[href + 6:html + 5]
    saveLog(blogUrl)

    if title == -1:
        print ' 遍历完毕,没有文章! '
    else:
        i = html
        while i < html + 1:
            title = con.find(r'<a title=', html)
            href = con.find(r'href=', title)
            html = con.find(r'.html', href)
            blogUrl = con[href + 6:html + 5]
            saveLog(blogUrl)
    j+=1



{% endhighlight %}

---
