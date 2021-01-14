---
layout: post
title: "Jekyll 博客 Markdown 的 Kramdown解析器"
subtitle: "编辑器常用语法"
date: 2021-01-13
author: "Carl"
mathjax: true
header-img: "img/post-bg.jpg"
tags: 
  - Tips
  - Markdown
  - Kramdown
  - LaTeX
---



### 简介

kramdown 是一个用Ruby实现的Markdown的解析器。

Markdown 是一种轻量型标记语言， 其目的在于为以网页为载体的文章的排版提供一种较 HTML 来说更简便、更安全、可读性更强的书写方式。它并不是HTML 的替代品，使用 Markdown 的语法编写的文章最终都要通过其翻译器转换成 HTML 代码。Github Pages 采用 Kramdown 解析器，所以当前这个博客是推荐使用这个语法。



> Kramdown	[官网链接](https://kramdown.gettalong.org/documentation.html)；	[语法文档中文翻译](http://pikipity.github.io/blog/kramdown-syntax-chinese-1.html)

> Markdown	[语法文档](https://daringfireball.net/projects/markdown/syntax)；	[ 中文说明文档PDF](http://alfred-sun.github.io/media/documents/MarkDown轻量级标记语言.pdf)



kramdown 语法是基于 Markdown 语法建立并加入了一些其他 Markdown 扩展版本（例如，Maruku、PHP Markdown Extra 和 Pandoc）所具有的特性。不仅如此，它努力去提供一个包括明确规则的严格的语法，所以它不可能完全符合 Markdown 语法。尽管如此，大多数用 Markdown 编写的文档依然可以用 kramdown 很好地解析。



### 源文件文本格式

一个 kramdown 文本可以支持多种编码格式，比如 ASCII、UTF-8 和 ISO-8859-1，并且会将他们转化为和你源文件同样的编码格式。



### Tab 的使用

krandown 定义 tab 是四个空格，当在在列表的行首空格使用 tab 的时候，这点非常重要。并且，tab 只可以在行首使用，不可以用来代替空格，否则结果不可预测。



### 自动和手动逃逸

根据输出的形式，有一些常用字符需要特别对待，比如，当将一个 kramdowmn 文档转化为 HTML 的时候，需要特别注意“<”、“>”和“&”字符。为了放别对这些特殊字符的处理，它们会正确地自动根据输出方式逃逸。

比如，你可以直接在 kramdown 文档中使用“<”、“>”和“&”字符，而不必去考虑它们在 HTML 中的使用。并且，如果你以 HTML 语言的形式或是 HTML 标签的形式使用使用这些字符的话，结果一样是正确的。

因为 kramdown 也是用了一些字符去标记文本，所以这里有一种方法去实现这种字符的逃逸，这样它们就是自己本来的意思了。这是使用反斜杠逃逸。比如，你可以类似这样来使用单引号：

```
This \`is not a code\` span!
```

下面是一个包含全部可以逃逸的字符的列表：

```
\         反斜线
.         点号
*         星号
_         下划线
+         加号
-         减号
=         等号
`         撇号
()[]{}<>  小、中、大括号、单书名号
#         井号
!         感叹号
<<        双小于
>>        双大于
:         冒号
|         单竖杠
"         双引号
'         单引号
$         钱的符号
```



### 块边界

一些块级元素必须以块边界来开始或是结束。这里有两种情况来使块边界发挥作用：

* 如果块级元素必须以块边界来开始，那么它必须是一个空行，一个 EOB 标记，或是一个断掉的 IAL 或者它就是第一个元素。
* 如果块级元素必须以块边界结束，那么它必须跟一个空行，一个 EOB 标记，或是一个断掉的 IAL 或者它就是最后元素。



### 空行

在 kramdown 中，任何一行只包含空字符例如空格或是 tab 就被认为是一个空行。一个或是多个连续的空行被认为是一个空行。空行被用来分割块级元素和其他部分，所以没有语义上的意思。

但是，这里还是有一些空行有寓意的情况：

+ 在标题使用时
+ 在代码块中使用时
+ 在列表中使用时
+ 在数学快中使用时
+ 在用来做一些元素的块边界的时候



### 段落

一个段落的第一行可以加入三个空格的缩进，其他行可以有任意数量的缩进，因为段落支持自动换行。但是需要补充的一点就是，当一个“定义列表行”出现的时候，一个段落会自动中断。

你可以用一个或多个空行来区分两个连续的段落。需要注意的是源文件中的一个空行并不意味着在输出文件中也是一个空行（因为“懒语法”）！如果你希望在输出中有一个空行（就好像 <br/> 标签），你需要在一行结束加上至少两个空格或是两个斜线！注意，一个段落的最后一行不可以是空行，这种空行会被忽略。开头和结尾的空格不会被纳入段落文字中。

下面给出的是一个段落效果的举例（`⋅`代表空格）：

```
This para line starts at the first column. However,
⋅⋅⋅⋅⋅⋅the following lines can be indented any number of spaces/tabs.
⋅⋅⋅The para continues here.

⋅⋅This is another paragraph, not connected to the above one. But⋅⋅
with a hard line break. \\
And another one.
```

效果如下：

This para line starts at the first column. However,
      the following lines can be indented any number of spaces/tabs.
   The para continues here.

  This is another paragraph, not connected to the above one. But  
with a hard line break. \\
And another one.



### 标题

krandown支持 “Setex” 和 “atx” 格式的标题。所有形式都可以在一个独立的文件中使用





### 公式



页面支持公式功能开启，在头文件添加：

```
mathjax: true
```



公式代码：

```latex
$$
f(n) =
\begin{cases}
0 && (n=0)\\
1 && (n=1)\\
f(n-1)+f(n-2) && (n\ge2)\\
\end{cases}
$$
```

效果：

$$
f(n) =
\begin{cases}
0 && (n=0)\\
1 && (n=1)\\
f(n-1)+f(n-2) && (n\ge2)\\
\end{cases}
$$



行内公式排版：

```
$ c = \sqrt{a^{2}+b_{0}^{2}+e^{x}} $
```

$ c = \sqrt{a^{2}+b_{0}^{2}+e^{x}} $

块公式排版：

```
$$ c = \sqrt{a^{2}+b_{0}^{2} +e^{x}} $$
```

$ c = \sqrt{a^{2}+b_{0}^{2} +e^{x}} $

LaTex的数学公式基本规则

```
$E = mc^2 $
$ \boxed{E=mc^2} $
$\fbox{E=mc^2}$
$\mathbf{E = mc^2}$
$\boldsymbol{E = mc^2}$
```

$E = mc^2 $
$ \boxed{E=mc^2} $
$\fbox{E=mc^2}$
$\mathbf{E = mc^2}$
$\boldsymbol{E = mc^2}$



```
$ H_{2}O $
```



$ H_{2}O $



```
$ X^2 $
```




$X^2$



```ruby
$$ \sideset{^1_2}{^3_4}\bigotimes $$
```

$$ \sideset{^1_2}{^3_4}\bigotimes $$

```cpp
$$x_{k}^2\quad \sqrt{x}\quad \sqrt[3]{x+y}$$
```

$$x_{k}^2\quad \sqrt{x}\quad \sqrt[3]{x+y}$$



若需要显示更大或更小的字符，在符号前插入 \large 或 \small 命令

```ruby
$A\large  A  \small A$
```

$A\large  A  \small A$



省略号\dots, \cdots,\vdots \ddots表示，\cdot常表示点乘，\vots是竖直方向的，\ddots是斜线方向的

```ruby
$$ x_1, x_2, \dots, x_n\quad 1,2,\cdots,n\quad \vdots\quad \ddots $$
```

$$x_1, x_2, \dots, x_n\quad 1,2,\cdots,n\quad \vdots\quad \ddots$$



分数与组合数

```ruby
$x = a _ 0 + \cfrac {1} {a _ 1
          + \cfrac {1} {a _ 2
          + \cfrac {1} {a _ 3 + \cfrac {1} {a _ 4} } } } 
$
```



$x = a _ 0 + \cfrac {1} {a _ 1
          + \cfrac {1} {a _ 2
                    + \cfrac {1} {a _ 3 + \cfrac {1} {a _ 4} } } } 
$



运算符



```ruby
$ \sum_{i=1}^n i $

$ \prod_{i=1}^n i$

$\lim_{x\to0}x^2 $

$\int_{a}^{b}x^2 dx $

$\sum\nolimits_{i=1}^n i \quad\prod\nolimits_{i=1}^n i
\quad
\lim\nolimits_{x\to0}x^2 \quad\int\limits_{a}^{b}x^2 dx 
$
```

$ \sum_{i=1}^n i $

$ \prod_{i=1}^n i$

$\lim_{x\to0}x^2 $

$\int_{a}^{b}x^2 dx $

$\sum\nolimits_{i=1}^n i \quad\prod\nolimits_{i=1}^n i
\quad
\lim\nolimits_{x\to0}x^2 \quad\int\limits_{a}^{b}x^2 dx 
$



括号的大小调整

```ruby
$\Bigg( \bigg( \Big( \big((x) \big) \Big) \bigg) \Bigg)$

$\Bigg\{ \bigg\{ \Big\{ \big\{\{x\} \big\} \Big\} \bigg\} \Bigg\}$
```

$\Bigg( \bigg( \Big( \big((x) \big) \Big) \bigg) \Bigg)$



$\Bigg\{ \bigg\{ \Big\{ \big\{\{x\} \big\} \Big\} \bigg\} \Bigg\}$



```ruby
$$ f(x,y,z) = 3y^2z \left( 3+\frac{7x+5}{1+y^2} \right) $$
```

$$f(x,y,z) = 3y^2z \left( 3+\frac{7x+5}{1+y^2} \right)$$



```swift
$$
f\left(
   \left[ 
     \frac{
       1+\left\{x,y\right\}
     }{
       \left(
          \frac{x}{y}+\frac{y}{x}
       \right)
       \left(u+1\right)
     }+a
   \right]^{3/2}
\right)
\tag{1.2}
$$
```

$$
f\left(
   \left[ 
     \frac{
       1+\left\{x,y\right\}
     }{
       \left(
          \frac{x}{y}+\frac{y}{x}
       \right)
       \left(u+1\right)
     }+a
   \right]^{3/2}
\right)
\tag{1.2}
$$





数学公式高级规则



```ruby
$\begin{equation}
f(x)=3x^{2}+6(x-2)-1
\end{equation}$
```

$\begin{equation}
f(x)=3x^{2}+6(x-2)-1
\end{equation}$



```ruby
$\begin{align}
 f(x) &= (x+a)(x+b) \\
 &= x^2 + (a+b)x + ab \tag{1.1}
\end{align}$
```

$\begin{align}
 f(x) &= (x+a)(x+b) \\
 &= x^2 + (a+b)x + ab \tag{1.1}
\end{align}$



```ruby
$\begin{align}
A_{1}&=B_{1}B_{2} & A_{3} & = B_{1}\\
A_{2}&=B_{3}& A_{3}A_{4} & = B_{4}
\end{align}$
```

$\begin{align}
A_{1}&=B_{1}B_{2} & A_{3} & = B_{1}\\
A_{2}&=B_{3}& A_{3}A_{4} & = B_{4}
\end{align}$



```latex
$$\begin{gather*}
E(X)=\lambda    \qquad  D(X)=\lambda    \\
E(\bar{X})=\lambda  \\
D(\bar{X})=\frac{\lambda}{n}    \\
E(S^2)=\frac{n-1}{n}\lambda \\
\end{gather*}$$
```

$$\begin{gather*}
E(X)=\lambda    \qquad  D(X)=\lambda    \\
E(\bar{X})=\lambda  \\
D(\bar{X})=\frac{\lambda}{n}    \\
E(S^2)=\frac{n-1}{n}\lambda \\
\end{gather*}$$



```
$\begin{equation}
 \left.\begin{aligned}
        B'&=-\partial \times E,\\
        E'&=\partial \times B - 4\pi j,
       \end{aligned}
 \right\}
 \qquad \text{Maxwell's equations}
\end{equation}
$
```

$\begin{equation}
 \left.\begin{aligned}
        B'&=-\partial \times E,\\
        E'&=\partial \times B - 4\pi j,
       \end{aligned}
 \right\}
 \qquad \text{Maxwell's equations}
\end{equation}
$



```latex
$\begin{equation}
\left.
\begin{aligned}
x+y &> 5 \\
y-y &> 11
\end{aligned}
\ \right\}\Rightarrow x^2 - y^2 > 55
\end{equation}$
```

$\begin{equation}
\left.
\begin{aligned}
x+y &> 5 \\
y-y &> 11
\end{aligned}
\ \right\}\Rightarrow x^2 - y^2 > 55
\end{equation}$



```latex
$$
\left\{ 
\begin{array}{c}
a_1x+b_1y+c_1z=d_1 \\ 
a_2x+b_2y+c_2z=d_2 \\ 
a_3x+b_3y+c_3z=d_3
\end{array}
\right. 
$$
```

$$
\left\{ 
\begin{array}{c}
a_1x+b_1y+c_1z=d_1 \\ 
a_2x+b_2y+c_2z=d_2 \\ 
a_3x+b_3y+c_3z=d_3
\end{array}
\right.
$$





```latex
$\begin{CD}
    A @>>> B @>{\text{very long label}}>> C \\
    @. @AAA @| \\
    D @= E @<<< F
\end{CD}$
```

$\begin{CD}
    A @>>> B @>{\text{very long label}}>> C \\
    @. @AAA @| \\
    D @= E @<<< F
\end{CD}$



https://www.jianshu.com/p/22117d964baf





$ 表示行内公式：

质能守恒方程可以用一个很简洁的方程式 `$ E=mc^2 $` 来表达：$ E=mc^2 $ 。

$$ 表示整行公式：

```
$$ \sum_{i=1}^n a_i=0 $$
$$ \sum^{j-1}_{k=0}{\widehat{\gamma}_{kj} z_k} $$
```

公式1

$$ \sum_{i=1}^n a_i=0 $$

公式2

$$ \sum^{j-1}_{k=0}{\widehat{\gamma}_{kj} z_k} $$


行间公式(Lorentz方程)：

```
$$
begin{aligned}
dot{x} &= sigma(y-x) \
dot{y} &= rho x - y - xz \
dot{z} &= -beta z + xy \
end{aligned}
$$
```

$$
begin{aligned}
dot{x} &= sigma(y-x) \
dot{y} &= rho x - y - xz \
dot{z} &= -beta z + xy \
end{aligned}
$$



在Markdown中将数学表达式放置在 $...$ 之间：

```
$\LaTeX{}$

$\Pi$

$ a * b = c ^ d $

$ 2^{\frac{n-1}{3}} $

$ \int\_a^b f(x)\,dx.$
```


效果：


$\LaTeX{}$

$\Pi$

$ a * b = c ^ d $

$ 2^{\frac{n-1}{3}} $

$ \int\_a^b f(x)\,dx.$





#### https://kramdown.gettalong.org/syntax.html



```
$$
\begin{aligned}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{aligned}
$$
```



效果：


$$
\begin{aligned}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{aligned}
$$


如上


|---
| Default aligned | Left aligned | Center aligned | Right aligned
|-|:-|:-:|-:
| First body part | Second cell | Third cell | fourth cell
| Second line |foo | **strong** | baz
| Third line |quux | baz | bar
|---
| Second body
| 2 line
|===
| Footer row


The above example table is rather time-consuming to create without the help of an ASCII table editor. However, the table syntax is flexible and the above table could also be written like this:



|-----------------+------------+-----------------+----------------|
| Default aligned |Left aligned| Center aligned  | Right aligned  |
|-----------------|:-----------|:---------------:|---------------:|
| First body part |Second cell | Third cell      | fourth cell    |
| Second line     |foo         | **strong**      | baz            |
| Third line      |quux        | baz             | bar            |
|-----------------+------------+-----------------+----------------|
| Second body     |            |                 |                |
| 2 line          |            |                 |                |
|=================+============+=================+================|
| Footer row      |            |                 |                |
|-----------------+------------+-----------------+----------------|


Here is an example for a kramdown table with a table header row, two table bodies and a table footer row:

* * *

---

_  _  _  _

---------------

Here are some example footer separator lines:

|====+====|
+====|====+
|=========|
|=


Here are some example header separator lines with alignment definitions:

|---+---+---|
+ :-: |:------| ---:|
| :-: :- -: -
:-: | :-


Here are some example separator lines:

|----+----|
+----|----+
|---------|
|-
| :-----: |
-|-


As mentioned at the beginning, an optional IAL for applying attributes to a term or a definition can be used:


{:#term} Term with id="term"
: {:.cls} Definition with class "cls"

{:#term1} First term
{:#term2} Second term
: {:.cls} Definition


The definition for a term is made up of text and/or block-level elements. If a definition is not preceded by a blank line, the first part of the definition will just be text if it would be a paragraph otherwise:

definition term
: This definition will just be text because it would normally be a
  paragraph and the there is no preceding blank line.

  > although the definition contains other block-level elements

: This definition *will* be a paragraph since it is preceded by a
  blank line.




As mentioned at the beginning, an optional IAL for applying attributes to a list item can be used after the list item marker:

  * {:.cls} This item has the class "cls".
    Here continues the above paragraph.

* This is a normal list item.



* kram
+ down
- now

1. kram
2. down
3. now



