---
layout: post
title: Python IDLE tab completion
categories:
- python
tags:
- python
---

> __#suprsvn:__ We can let the Python IDLE support 'tab completion'.

---

## 1.Put the codes into a file named '.pythonstartup'.

{% highlight python %}

import pdb
# python startup file
import readline
import rlcompleter
import atexit
import os
# tab completion
readline.parse_and_bind('tab: complete')
# history file
histfile = os.path.join(os.environ['HOME'], '.pythonhistory')
try:
    readline.read_history_file(histfile)
except IOError:
    pass
atexit.register(readline.write_history_file, histfile)
del os, histfile, readline, rlcompleter

{% endhighlight %}

---

## 2. Put the file into your HOME directory.      

    Linux: ~/.pythonstartup
    Windows: C:\Users\USERNAME\.pythonstartup

---

## 3. Set the Environment Variables.       

In Windows:Just do it like this.

![PYTHONSTARTUP](./images/PYTHONSTARTUP.png)

In Linux:Put the line into the file named '.profile'.

    export PYTHONSTARTUP=~/.pythonstartup     

---

## Previews:

![python_idle_tab_completion.gif](./images/python_idle_tab_completion.gif)

---

### OvEr … :-) …

---
