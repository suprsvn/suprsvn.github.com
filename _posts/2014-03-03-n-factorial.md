---
layout: post
title: n!末尾有多少个零
categories:
- python
tags:
- python
---

> __#suprsvn:__ 今天看到一个经典的算法问题：n的阶乘n!末尾有多少个零？

---

## 算法一：     

    各位用此算法计算一下`987654321!`末尾有多少个零~~  `:-)`

{% highlight python %}

def func1(n):
    ret = 0
    for i in range(1, n + 1):
        j = i
        while(j % 5 == 0):
            ret = ret + 1
            j /= 5
        i = i + 1
    return ret

print func1(987654321)

{% endhighlight %}

### 莫怪，不出意外的话，你的PC死机了。。。
### 开个玩笑而已，谁让你不分析一下算法就直接复制粘贴呢？
### 这个算法不能用，效率低到让PC死机。

---

## 算法二：     


{% highlight python %}

def func2(n):
    count = 0
    while n / 5 > 0:
        count += n / 5
        n = n / 5
    return count

print func2(987654321)

{% endhighlight %}

### 这个算法才是最优的，仔细分析一下吧。

---

### OvEr … :-) …

---