---
layout: post
title: vim中按tab跳出括号引号
categories:
- vim
---

> __#suprsvn:__ 在vim中，当括号引号补全后，总是需要再次敲出后半部分，光标才能跳出，下面的方法可以在括号引号中直接按tab键，光标跳出括号引号，多层括号引号，可以多按几次，依次跳出。

---

## 将下面的配置信息加入到vim的配置文件中，linux下该文件在`～/.vimrc`。

{% highlight python %}

"" Out of the brackets 
func SkipPair()
    if getline('.')[col('.') - 1] == ')' || getline('.')[col('.') - 1] == ']' || getline('.')[col('.') - 1] == '"' || getline('.')[col('.') - 1] == "'" || getline('.')[col('.') - 1] == '}'
        return "\<ESC>la"
    else
        return "\t"
    endif
endfunc
inoremap <TAB> <c-r>=SkipPair()<CR>

{% endhighlight %}

---

## 看一下效果。


![jump-out-the-brackets-by-tab](http://0nly.me/images/jump-out-the-brackets-by-tab.gif)


---

### OvEr … :-) …

---
