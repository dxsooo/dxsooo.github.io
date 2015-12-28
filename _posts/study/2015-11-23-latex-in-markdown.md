---
layout: post
title: Markdown中插入LaTeX数学公式的方法
tags:
  - Markdown
  - LaTeX
  - MathJax
category: Study
image: http://i63.tinypic.com/2s64q2r.png
description: Markdown自由书写的特性很好，但遇到数学公式时就要煞费苦心——每次都是先使用LaTeX书写，然后保存为图片，使用img标签进行引用，当公式很多的时候稍显复杂。本文的方法使用html的语法，在线生成LaTeX数学公式，免去将公式保存为图片的麻烦。当然，弊端也是有的，公式太多，可能会造成刷新比一般的网页慢一些。
math: true
toc: true
---

Markdown刚兴起的时候没太在意，没想到自己为了搭建博客也慢慢用起来了。现在使用Markdown+Github Pages发文章，还是挺顺利的。

最近又开始学习LaTeX，要用Markdown做笔记就遇到麻烦了，不过没关系，万能的搜索引擎分分钟搞定。

下面介绍的方法使用html的语法，在网页中自动生成LaTeX数学公式，免去将公式保存为图片的麻烦。当然，弊端也是有的，公式太多，可能会造成刷新比一般的网页慢一些，而且现在不太懂LaTex，用起来还不顺手。

### 方法一：使用Google Chart的服务器

{% highlight html %}
<img src="http://chart.googleapis.com/chart?cht=tx&chl= 在此插入LaTex公式" style="border:none;">
{% endhighlight %}

举个例子：

{% highlight html %}
<img src="http://chart.googleapis.com/chart?cht=tx&chl=\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" style="border:none;">
{% endhighlight %}

公式显示结果为：

<img src="http://chart.googleapis.com/chart?cht=tx&chl=\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" style="border:none;">

Google Chart服务器的响应速度还可以，但据说可能复杂一些的LaTeX公式可能无法解析。

### 使用forkosh服务器

forkosh上提供了关于LaTeX公式的一份简短而很有用的帮助，使用forkosh插入公式的方法是：

{% highlight html %}
<img src="http://www.forkosh.com/mathtex.cgi? 在此处插入LaTex公式">
{% endhighlight %}

同样一个例子：

{% highlight html %}
<img src="http://www.forkosh.com/mathtex.cgi? \Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}">
{% endhighlight %}

显示结果为：

<img src="http://www.forkosh.com/mathtex.cgi? \Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}">

因为网页插入公式的原理是调用“某某网站的服务器”动态生成的，所有保证公式正常显示的前提是该网址能一直存在着为我等小生做些小小的服务。

### 方法三：使用MathJax引擎

大家应该看过[Stackoverflow](http://stackoverflow.com/)上的公式吧，其生成的不是图片。这就要用到[MathJax](https://www.mathjax.org/)引擎，在Markdown中添加MathJax引擎也很简单，先添加一段`javascript`：

{% highlight javascript %}
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
{% endhighlight %}

然后，再使用TeX/LaTex写公式。`$$公式$$`表示行间公式，本来TeX中使用`\(公式\)`表示行内公式，但因为Markdown中`\是`转义字符，所以在Markdown中输入行内公式使用`\\(公式\\)`，如下代码：

~~~
$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$
\\(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}\\)
~~~

分别显示结果（行间公式）：

$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$

行内公式：\\(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}\\)

你还可以试一下，公式上还可以使用鼠标右键操作，比如说直接保存TeX命令等。
