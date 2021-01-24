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



### atx 风格标题 {#header}

```
~~~
#         一级
##
###
####
#####
######    六级
~~~
```



### 指定标头ID（`{#head_id}`） 

```html+django
~~~

###### I can help you  {#head_1}

HTML 内代码：
<h6 id="head_1">I can help you</h6>
~~~
```

### 引用 {#Blockquotes}

```
~~~
> 引用文本
~~~

#### kramdown中 | 会被渲染，需要转义

> 引用文本\|单行

> 使用 `<br>` or 两个空格可  
> 以换行
```

### 空行 {# blank_line}

```text
`<br>` or 两个空格
```

### Code {#code}

```text
~~~
# Code
~~~

> 若Code内含有 "~" 符号，则只需要将 三个 **启动符号 "~"** 号多写几个就可以：
```

### 清单 {#Definition_Lists}

```abap
~~~
* kram
+ down
- now

1. kram
2. down
3. now
~~~

> 注意缩进
```

### 表格 {#Tables}

```text
~~~
| Header One     | Header Two     |
| :------------- | :------------- |
| Item One       | Item Two       |
~~~
```

### 分割线 {#Horizontal_Rules}

```text
~~~
* * *

---

  _  _  _  _

---------------
~~~
```

### HTML块 {#html_blocks}

```html+django
> 如果HTML标记具有属性markdown="0"，则标记将被解析为原始HTML块。  
> 如果HTML标记具有属性markdown="1"，则使用此标记中用于解析语法的默认机制。  
> 如果HTML标记具有属性markdown="block"，则标记的内容将被解析为块级元素。  
> 如果HTML标记具有属性markdown="span"，则标记的内容将被解析为span级别元素

~~~ html
script style math option textarea pre code kbd samp var
~~~

> 解析为原始 HTML

~~~ html
applet button blockquote body colgroup dd div dl fieldset form iframe li
map noscript object ol table tbody thead tfoot tr td ul
~~~

> 解析为块级元素

~~~ html
a abbr acronym address b bdo big cite caption code del dfn dt em
h1 h2 h3 h4 h5 h6 i ins kbd label legend optgroup p pre q rb rbc
rp rt rtc ruby samp select small span strong sub sup th tt var
~~~

> 解析为 span 级元素

~~~ html
<div markdown="1">This is the first part of a para,
which is continued here.
</div>
~~~
```

### 链接和图像 {#link_img}

```text
~~~
# 自动链接(尖括号)
<me.example@example.com>

# 内联链接
[link](http://xxx.com)


# 图片
![img](http://xxx/1.img)

# 由于可以通过span和块IAL添加其他属性，因此可以指定图像宽度和高度
![smiley](http://xxx/1.img){:height="36px" width="36px"}
~~~
```

### 重点 {#Emphasis}

```text
~~~
*some text*
_some text_
**some text**
__some text__
~~~

# kramdown中单个 * 会被渲染，需要转义 \*
```

### 单行代码 {#line_code}

```python
~~~
`code`
~~~

~~~
# 与代码块一样，可以使用IAL设置代码范围的语言

This is a Ruby code fragment `x = Class.new`{:.language-ruby}

`import re`{:.language-python}
~~~
```

### 脚注 {#Footnotes}

```text
~~~
人有悲欢离合，月有阴晴圆缺.[^1]

[^1]: 《水调歌头》
~~~
```

### 缩略语 {#Abbreviations}

```text
~~~
*[another language]: It's called Markdown

*[WTF]: What the fuck
~~~
```

### 属性列表定义 {#Attribute-List-Definitions}

```abnf
> 用于向块和 span级元素添加属性

~~~
# 例子:
{:ref-name: #myid .my-class}
{:other: ref-name #id-of-other title="hallo you"}
{:test: key="value \" with quote" and other='quote brace \}'}
~~~

~~~
# ALD行具有以下结构：

左括号，可选前面最多三个空格，
然后是冒号，引用名称和另一个冒号，
然后是属性定义（允许的字符是反斜杠转义关闭括号或除了未转义的右括号之外的任何字符），
然后是一个右括号和可选空格，直到行尾
~~~

> 引用名称需要以单词字符或数字开头，可选地后跟其他单词字符，数字或短划线  
> 有四种不同类型的属性定义，必须用一个或多个空格分隔

> 如果不存在具有此引用名称的属性定义列表，则在收集属性时将忽略引用名称

~~~
# 以下ALD都是等效的：

{:id: .cls1 .cls2}
{:id: class="cls1" .cls2}
{:id: class="something" class="cls1" .cls2}
{:id: class="cls1 cls2"}
~~~
```

### 内联属性列表 {#Inline-Attribute-Lists}

```text
> 此块级元素用于将属性附加到另一个块级元素  
> 块内联属性列表（块IAL）具有与ALD相同的结构

> 块IAL（或两个或多个块IAL）必须直接放在属性应附加到的块级元素之前或之后。  
> 如果块IAL直接在块级元素之后和之前，则将其应用于前一元素。在所有其他情况  
> 下，块IAL被忽略，例如，当块IAL被空行包围时

> 在引用的ALD中，IAL的键值对 **优先于同名的键值对**


~~~
# 以下是块IAL的一些示例：

A simple paragraph with an ID attribute.
{: #para-one}

> A blockquote with a title
{:title="The blockquote title"}
{: #myid}

{:.ruby}
    Some code here
~~~
```

### Span 内联属性列表 {#span_ial}

```text
> span 级元素的块内联属性列表的一个版本

> 它具有与块IAL相同的结构，除了不允许前导和尾随空格  
> 跨度IAL（或两个或更多跨度IAL）必须直接放在应该应  
> 用它的span-level元素之后，之间不允许有其他字符，否则它将被忽略并仅从输出中删除


~~~
This *is*{:.underline} some `code`{:#id}{:.class}.
A [link](test.html){:rel='something'} and some **tools**{:.tools}.
~~~
```

### 扩展 {#Extensions}

```text
> 扩展提供了其他功能，但使用相同的语法。它们既可以作为块也可以作为跨度级元素使用   
>扩展的语法与ALD的语法非常相似

~~~
# 示例

{::comment}
This text is completely ignored by kramdown - a comment in the text.
{:/comment}

Do you see {::comment}this text{:/comment}?
{::comment}some other comment{:/}

{::options key="val" /}
~~~

- 一个左大括号，
- 接着是两个冒号和扩展名，
- 可选地后跟空格和属性定义（允许的字符是反斜杠转义关闭括号或除了未转义的右括号之外的任何字符|同ALD
- 然后是斜线和右大括号（如果扩展没有正文）或只有右大括号（如果扩展有正文）

~~~
# kramdown可以使用以下扩展名：

comment
将正文文本视为未在输出中显示的注释

nomarkdown
不要使用kramdown处理主体，而是按原样输出。该属性type指定哪些转换器应输出正文：如果缺少该属性，则所有转换器都应输出该属性。否则，属性值必须是以空格分隔的转换器名称列表，并且这些转换器应输出正文。

options
由于正文被忽略，应该在没有正文的情况下使用。用于设置kramdown处理器的全局选项（例如，禁用自动标头ID生成）。请注意，解析器使用的选项立即生效，而所有其他选项都不是！这意味着，例如，不能仅为kramdown文档的某些部分设置转换器选项
~~~
```





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



