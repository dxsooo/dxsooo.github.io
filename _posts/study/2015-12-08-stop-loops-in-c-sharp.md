---
layout: post
title: C#中循环的中断
tags:
    - C#
category: Study

image: http://i65.tinypic.com/vhry95.jpg
description: C#中，有时候需要精细地控制循环代码的处理，那就要用到下面四种循环控制语句。
---

C#中，有时候需要精细地控制循环代码的处理，那就要用到下面四种循环控制语句。

* break——立即终止循环；
* continue——立即终止当前循环，继续执行下一次循环；
* goto——可以跳出循环，到已经标记好的位置上（不想跳来跳去看代码的话，尽量少用该命令）；
* return——跳出循环及其包含的函数。

> `break`命令可以跳出当前循环，继续执行循环后面的第一行代码。

例如下面的代码：

{% highlight c# %}
int i = 1;
while (i <= 10)
{
  if (i == 6)
    break;
  Console.WriteLine("{0}", i++);
}
{% endhighlight %}

这段代码输出1~5的数字，因为`break`命令在`i`的值为6时退出循环。

> `continue`仅终止当前的循环，而不是整个循环。

例如：

{% highlight c# %}
int i;
for (i = 1; i <= 10; i++)
{
  if ((i % 2) == 0)
    continue;
  Console.WriteLine(i);
}
{% endhighlight %}

在上面的例子中，只要`i`除以2的余数是0，`continue`语句就终止当前的循环，所以最终显示的数字是1、3、5、7和9。

> 使用`goto`语句退出循环是合法的，但使用`goto`从外部进入循环是非法的。
