---
layout: post
category: Tips
title: 解决网页打印预览空白的问题
tags: printer
image: http://i66.tinypic.com/1qjvj4.jpg
description: 有时候想打印一个网页，可是预览的时候显示为空白，很妨碍自己估计打印效果。这种情况，多半是由于保护模式下 %Temp%\Low 这个文件夹工作不正常引起的（被误删除、移位等等）。
---

有时候想打印一个网页，可是预览的时候显示为空白，很妨碍自己估计打印效果。这种情况，多半是由于保护模式下`%Temp%\Low`这个文件夹工作不正常引起的（被误删除、移位等等）。

这里介绍两种解决方法：

* 方法一：IE 重置，直接还原为厂商默认设置。这个最是简单省事了！具体步骤，请参考 易宝典: 如何重置 IE 设置？ (http://support.microsoft.com/kb/981061/zh-cn)

* 方法二：新建Low文件夹并设置其低完整性级别。不方便重置？没关系，看看第二种方法详解吧。打开开始，在最下端搜索框输入cmd，然后以管理员身份运行cmd， 在命令提示符处键入以下命令，然后按回车键：

~~~
Mkdir %TEMP%\Low

ICACLS “%Temp%\Low” /setintegritylevel (OI)(CI)low
~~~
