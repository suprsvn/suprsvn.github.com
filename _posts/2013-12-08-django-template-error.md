---
layout: post
title: Django Template 报错
categories:
- python
tags:
- django
---

> __#suprsvn:__ 学习和使用python也好久了，也想进阶一下，学习python的web开发框架django。关于django的学习还是电子书pdf为辅，动手敲字母为主。我参考的电子书之前分享过，下载请参见[《经典python电子书分享》](http://0nly.me/2013/12/python-pdf/)一文。

---

### 错误图：

![错误图](http://suprsvn.qiniudn.com/codelog/django-template-error.png)

###error文字描述摘录：

    django.core.exceptions.ImproperlyConfigured: Requested setting TEMPLATE_DEBUG, but settings are not configured. You must either define the environment variable DJANGO_SETTINGS_MODULE or call settings.configure() before accessing settings.

---

### 报错原因：

*直接python命令启动python交互式解释器,导入django template会报错*

---

### 解决方法一：*先导入settings*
  
    >>> from django.conf import settings    
    >>> settings.configure()  

### 解决方法二：*使用python manage.py shell启动Python交互式解释器(实际上启动的是Ipython)*
  
    $python manage.py shell
  
---

### OvEr … :-) …

---
