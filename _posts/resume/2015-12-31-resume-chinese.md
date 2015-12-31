---
layout: post
title: Resume
tags:
    - Resume
category: Resume

image: http://i63.tinypic.com/219uebs.png
description: 无论是什么类型的变量，所有的数据都是一些列的位，即一系列的0和1。变量的含义是通过解释这些数据的表达方式来传达的。但一般情况下，不同类型的变量使用不同的模式来表示数据。有时需要对数据进行类型转换，就需要采用今天介绍的类型转换方法。
---

无论是什么类型的变量，所有的数据都是一些列的位，即一系列的0和1。变量的含义是通过解释这些数据的表达方式来传达的。但一般情况下，不同类型的变量使用不同的模式来表示数据。有时需要对数据进行类型转换，就需要采用今天介绍的类型转换方法。

C#中类型转换有以下两种形式：

* **隐式转换**：从类型A到类型B的转换可以在所有情况下进行，执行转换的规则非常简单，由编译器自动执行转换。

* **显式转换**：从类型A到类型B的转转只能在某些情况下进行，转换规则比较复杂，应进行某种类型的处理。

## 隐式转换

隐式转换不需要做任何工作，也不需要另外编写代码。例如，`ushort`和`char`的值是可以相互转换的，它们都可以存储在`0~65535`之间，在这两个类型之间就可以进行隐式转换。

{% highlight c# %}
ushort dest;
char source = 'a';
dest = source;
Console.WriteLine("Source value: {0}", source);
Console.WriteLine("Destination value: {0}", dest);
{% endhighlight %}

上面的示例得到的结果是：

~~~
Source value: a
Destination value: 97
~~~

所以说，即使两个变量存储的是相同的信息，使用不同的类型解释它们时，方式也是不同的。而任何类型A，只要其取值范围完全包含在类型B的取值范围中，就可以隐式转换为类型B。

值得注意的是：`char`存储的是数值，而`bool`和`string`没有隐式转换。

## 显式转换

显式转换明确要求编译器把数值从一种类型转换为另一种数据类型。因此，需要另外编写代码，代码的格式将随着转换方法而异，但基本语法是：

~~~
<(destinationType)sourceVar>
~~~

这将把`sourceVar`中的值转换为`destinationType`。例如把`short`变量强制转换为`byte`：

{% highlight c# %}
byte dest;
short source = 7;
dest = (byte)source;
{% endhighlight %}

那么，试图把一个值转换为不合适的变量的时候，会发生什么呢？比如下面的代码：

{% highlight c# %}
byte dest;
short source = 281;
dest = (byte)source;
Console.WriteLine("Source value: {0}", source);
Console.WriteLine("Destination value: {0}", dest);
{% endhighlight %}

其结果如下：

~~~
Source value: 281
Destination value: 25
~~~

看看结果数值的二进制表示，以及byte中最大值255的二进制表示：

~~~
281 = 100011001
 25 = 000011001
255 = 011111111
~~~

从上面可以看出，源数据281的最左边一位丢失了。显然，当显式地把一种数据类型转换为另一种数据类型时，最好能了解是否有数据丢失，如果不知道，就会发生严重问题。

这里要用到两个关键字：`checked`和`unchecked`，称为表达式的溢出检查上下文。

{% highlight c# %}
byte dest;
short source = 281;
dest = checked((byte)source);
{% endhighlight %}

执行上面这段代码时，程序就会崩溃，如果用`unchecked`替代上面的`checked`，就会得到之前一样的结果，不会报错。

除了上面两个关键字外，还可以在`Visual Studio`中配置，让这种类型的表达式都包含`checked`关键字。

## 使用Convert命令进行显式转换

例如`Convert.ToDouble()`命令，可以把字符串转换为数值，为了成功执行此类转换，所提供的字符串必须是有效的表达式，该数还必须是不会溢出的数。按这种方式可以进行许多显式转换，如下表：

<table>
<tr>
<th style="width:5%;">Sr.No</th>
<th>Methods &amp; Description</th>
</tr>
<tr>
<td>1</td>
<td><b>ToBoolean</b>
<p>Converts a type to a Boolean value, where possible.</p>
</td>
</tr>
<tr>
<td>2</td>
<td><b>ToByte</b>
<p>Converts a type to a byte.</p>
</td>
</tr>
<tr>
<td>3</td>
<td><b>ToChar</b>
<p>Converts a type to a single Unicode character, where possible.</p>
</td>
</tr>
<tr>
<td>4</td>
<td><b>ToDateTime</b>
<p>Converts a type (integer or string type) to date-time structures.</p>
</td>
</tr>
<tr>
<td>5</td>
<td><b>ToDecimal</b>
<p>Converts a floating point or integer type to a decimal type.</p>
</td>
</tr>
<tr>
<td>6</td>
<td><b>ToDouble</b>
<p>Converts a type to a double type.</p>
</td>
</tr>
<tr>
<td>7</td>
<td><b>ToInt16</b>
<p>Converts a type to a 16-bit integer.</p>
</td>
</tr>
<tr>
<td>8</td>
<td><b>ToInt32</b>
<p>Converts a type to a 32-bit integer.</p>
</td>
</tr>
<tr>
<td>9</td>
<td><b>ToInt64</b>
<p>Converts a type to a 64-bit integer.</p>
</td>
</tr>
<tr>
<td>10</td>
<td><b>ToSbyte</b>
<p>Converts a type to a signed byte type.</p>
</td>
</tr>
<tr>
<td>11</td>
<td><b>ToSingle</b>
<p>Converts a type to a small floating point number.</p>
</td>
</tr>
<tr>
<td>12</td>
<td><b>ToString</b>
<p>Converts a type to a string.</p>
</td>
</tr>
<tr>
<td>13</td>
<td><b>ToType</b>
<p>Converts a type to a specified type.</p>
</td>
</tr>
<tr>
<td>14</td>
<td><b>ToUInt16</b>
<p>Converts a type to an unsigned int type.</p>
</td>
</tr>
<tr>
<td>15</td>
<td><b>ToUInt32</b>
<p>Converts a type to an unsigned long type.</p>
</td>
</tr>
<tr>
<td>16</td>
<td><b>ToUInt64</b>
<p>Converts a type to an unsigned big integer.</p>
</td>
</tr>
</table>

对于这些转换，它们总是要进行溢出检查的，`checked`和`unchecked`关键字和项目属性设置不起作用。
