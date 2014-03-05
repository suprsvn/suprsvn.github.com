---
layout: post
title: 右键用Sublime Text打开文件
categories:
- tools
---

> __#suprsvn:__ Sublime Text是写代码的神器，在下载的时候大多数都是下载`portable version`的Sublime，虽然绿色快速并且易于破解，但是在编辑文本或脚本的时候没有鼠标右键`用Sublime Text打开`的快捷选项。

---

###新建一个txt文本文档加入下面的代码，然后重命名为`sublime.reg`(扩展名要由.txt改为.reg)。双击导入注册表即可。     

{% highlight python %}

[HKEY_CLASSES_ROOT\*\shell\Sublime2]
@="用Sublime Text打开"

[HKEY_CLASSES_ROOT\*\shell\Sublime2\command]
@="\"D:\\softwares\\Sublime Text 3\\sublime_text.exe\" -p --remote-tab-silent \"%1\""

{% endhighlight %}

### 注意：`D:\\softwares\\Sublime Text 3\\sublime_text.exe`要替换为你的Sublime Text的路径，并且路径中要用`双\`     

---

### OvEr … :-) …

---