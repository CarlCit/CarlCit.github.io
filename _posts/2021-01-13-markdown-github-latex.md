---
layout: post
title: "Jekyll 编辑 Markdown 使用 LaTeX 公式"
subtitle: "公式编辑开启及测试"
date: 2021-01-13
author: "Carl"
mathjax: true
header-img: "img/post-bg.jpg"
tags: 
  - Tips
  - LaTeX
  - Markdown
  - Kramdown
---



公式开启

头文件添加

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

\$$f(n) = \begin{cases}0 && (n=0)\\1 && (n=1)\\f(n-1)+f(n-2) && (n\ge2)\\\end{cases}$$



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

上下标及常用符号

```
$y_N$
$y_{_N}$
```

$y_N$ , 
$y_{_N}$

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
$$ x_{k}^2\quad \sqrt{x}\quad \sqrt[3]{x+y} $$
```

$$ x_{k}^2\quad \sqrt{x}\quad \sqrt[3]{x+y} $$



若需要显示更大或更小的字符，在符号前插入 \large 或 \small 命令

```ruby
$A\large  A  \small A$
```

$A\large  A  \small A$



省略号\dots, \cdots,\vdots \ddots表示，\cdot常表示点乘，\vots是竖直方向的，\ddots是斜线方向的

```ruby
$$ x_1, x_2, \dots, x_n\quad 1,2,\cdots,n\quad \vdots\quad \ddots $$
```

$$ x_1, x_2, \dots, x_n\quad 1,2,\cdots,n\quad \vdots\quad \ddots $$



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

$$ f(x,y,z) = 3y^2z \left( 3+\frac{7x+5}{1+y^2} \right) $$



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



