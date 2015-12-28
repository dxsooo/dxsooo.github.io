---
layout: post
category: Tips
title: Office (Word) 2016中手动加载Endnote X7.4
tags: Endnote
image: http://i66.tinypic.com/5n1z4k.png
description: 电脑升级到Windows 10之后，顺便把Office也升级到2016版Office 365，可即便Endnote已更新到最新版本，Word中也没有CWYW的选项卡，这里就介绍如何使用Endnote官方的补丁手动注册Endnote的CWYW选项卡。
---

电脑升级到Windows 10之后，顺便把Office也升级到2016版Office 365，可即便Endnote已更新到最新版本，Word中也没有CWYW的选项卡，这里就介绍如何使用Endnote官方的补丁手动注册Endnote的CWYW选项卡。

Endnote在官网给出了一个补丁：[http://endnote.com/kb/137576](http://endnote.com/kb/137576)，里面也给出了详细的说明，请注意该说明中提到的资源在上述网页的右边栏中下载，或者是从我下面给出的链接中下载。

这里给大家引用一下官方的说明：

1. Launch Word 2016.
2. In Word’s ribbon tab, select “File”, then “Account”, and then click “About Word” button.  The end of the first line indicates the architecture (32-bit or 64-bit) of this installation of Microsoft Word.  Close Microsoft Word after you have checked this.
3. Please on the right side download the “X74_CWYW_X86.zip” if you are using Microsoft Word 32-bit, or “X74_CWYW_X64.zip” if you are using Microsoft Word 64-bit.
4. Right click the downloaded zip file, and select “Extract All…”, and extract it to a temporary location you like (i.e. Desktop).  After the extraction, it will open an Explorer window, with a folder “ResearchSoft” in it.
5. Move the “ResearchSoft” folder inside that folder to the appropriate Common Program Files folder depends on your system:

    \* If you are running 32-bit version of Windows there is no “C:\Program Files (x86)”, move the “ResearchSoft” folder to:
C:\Program Files\Common Files

    \* If you are running 64-bit version of Windows, and you downloaded X74_CWYW_X86.zip (for Word 2016 32-bit), move the “ResearchSoft” folder to:
C:\Program Files (x86)\Common Files

    \* If you are running 64-bit version of Windows, and you downloaded X74_CWYW_X64.zip (for Word 2016 64-bit), move the “ResearchSoft” folder to:
C:\Program Files\Common Files

    \* Select “Continue” if you are prompted to provide administrative permission to move the folder.

6. Double click the “ResearchSoft” folder in Common Program Files folder, then “Cwyw”, and then “17”.
7. Right click the “InstallCWYW.bat”, and select “Run as administrator”, and click “Yes” in the User Account Control elevation prompt.
8. Launch Word again, you should see the “EndNote X7” or “EndNote” ribbon tab, depends on whether you have EndNote X7 installed, and have selected the EndNote X7 or EndNote online tools.

---
简单说来，就是先要确定自己的Office (Word)版本，看你装的是32位还是64位的Office，然后根据情况下载下面其中一个资源：

* [X74_CWYW_X86.zip](http://kbportal.thomson.com/utility/getfile.aspx?rid=7645)
* [X74_CWYW_X64.zip](http://kbportal.thomson.com/utility/getfile.aspx?rid=7646)

下载完后，解压缩到自己喜欢的位置，里面包含一个`ResearchSoft`的文件夹，将这个文件夹移动到系统相应的`Common Files`文件夹中：

* 如果你使用32位的Windows系统，就移动到`C:\Program Files\Common Files`
* 如果你使用64位的Windows系统，但是安装的是32位Office软件，就移动到`C:\Program Files (x86)\Common Files`
* 如果你使用64位的Windows，并安装的是64位的Office，那就移动到`C:\Program Files\Common Files`

然后双击打开`ResearchSoft`文件夹，再打开`CWYW`，接着打开`17`文件夹。

右击`InstallCWYW.bat`并选择管理员模式运行，在弹出的窗口中单击`确定`。这样就完成了Endnote CWYW选项卡的注册，重启Office (Word)就可以照常使用了。相信过不久Endnote更新会自动更新这一块的。
