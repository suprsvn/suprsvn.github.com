---
layout: post
title: Vim自动关闭函数即开式预览scratch preview
categories:
- vim
---

![Vim的scratch preview窗口](http://suprsvn.qiniudn.com/codelog/vim-scratch-preview.png)

###我在python一下的时候，Vim中使用了omnifunc=pythoncomplete插件，补全很爽，但是出现了本文所要解决的小问题：

***补全函数后，函数即开式预览一直开启，需要手动`:q`关闭***

###这样搞的码起来很是不爽。

> 解决方法参考了国外的一个[帖子](http://stackoverflow.com/questions/3105307/how-do-you-automatically-remove-the-preview-window-after-autocompletion-in-vim)
> 这里我简单的用中文记录一下。

##方法1：在`~/.vimrc`中加入下面两行设置，实现***离开补全弹窗或者离开插入模式***时自动关闭scratch preview。

    autocmd InsertLeave * if pumvisible() == 0|pclose|endif
    autocmd CursorMovedI * if pumvisible() == 0|pclose|endif

##方法2：如果已使用了`supertab`插件,可以在`~/.vimrc`中加入设置实现tab键关闭scratch preview。

    let g:SuperTabClosePreviewOnPopupClose = 1

##方法3：：在`~/.vimrc`中加入下面设置，也可以实现***方法1***中的效果。
    
    augroup GoAwayPreviewWindow
    autocmd! InsertLeave * wincmd z
    augroup end

### ***oVeR ... :-)...***

---

