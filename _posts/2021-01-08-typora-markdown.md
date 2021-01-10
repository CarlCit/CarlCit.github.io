---
layout: post
title: "Typora 的 Markdown 使用语法格式"
subtitle: "编辑器 Typora 中如何使用 Markdown 语法"
date: 2021-01-08
author: "Carl"
header-img: "img/post-bg.jpg"
header-mask: 0.3
mathjax: true
tags: 
  - Typora
  - Markdown
  - application
---



# Markdown 规范参考

2016年1月1日 通过 [typora.io](http://typora.io)

[官方原文链接](https://support.typora.io/Markdown-Reference/)

##  概观

**Markdown** 由 [Daring Fireball](http://daringfireball.net/) 创建; 原始指南就[在这里](https://daringfireball.net/projects/markdown/syntax)。但是，它的语法因不同的解析器或编辑器而异。**Typora** 正在使用 [GitHub ](https://help.github.com/articles/github-flavored-markdown/) **Flavored**  [Markdown](https://help.github.com/articles/github-flavored-markdown/) 。

##  块元素

###  段落和换行符

段落只是一行或多行连续的文本。在 markdown 源代码中，段落由两个或多个空行分隔。在 Typora 中，您只需要一个空行（按 `Return`一次）即可创建一个新段落。

按 `Shift`+ `Return` 可创建单个换行符。大多数其他降价解析器将忽略单换行符，因此为了使其他降价解析器识别换行符，您可以在行的末尾留下两个空格，或者插入 `<br/>`。

###  头

标题 `#` 在行的开头使用 1-6个hash（）字符，对应于标题级别1-6。例如：

```
# This is an H1

## This is an H2

###### This is an H6
```

在 Typora 中，输入’＃'后跟标题内容，`Return` 按键将创建标题。

###  引用文字

Markdown 使用电子邮件样式>字符进行块引用。它们表示为：

```ruby
> This is a blockquote with two paragraphs. This is first paragraph.
>
> This is second pragraph. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.



> This is another blockquote with one paragraph. There is three empty line to seperate two blockquote.
```

在 Typora 中，输入 ‘>’ 后跟您的引用内容将生成一个引用块。Typora 将为您插入正确的 “>” 或换行符。通过添加额外级别的 “>” 嵌套块引号（另一个块引用内的块引用）。

###  清单

输入 `* list item 1` 将创建一个无序列表 - `*` 符号可以替换为`+`或`-`。

输入 `1. list item 1` 将创建一个有序列表 - 其降序源代码如下：

```ruby
## un-ordered list
*   Red
*   Green
*   Blue

## ordered list
1.  Red
2. 	Green
3.	Blue
```

###  任务列表

任务列表是标记为 [] 或 [x] （不完整或完整）的项目的列表。例如：

```ruby
- [ ] a task list item
- [ ] list syntax required
- [ ] normal **formatting**, @mentions, #1234 refs
- [ ] incomplete
- [x] completed
```

您可以通过单击项目前面的复选框来更改完整/不完整状态。

- [x] completed

###  （受控）代码块

Typora 仅支持 GitHub Flavored Markdown 中的栅栏。不支持 markdown 中的原始代码块。

使用栅栏很简单：输入

```cpp
[```]
```

然后按 return。在之后添加一个可选的语言标识符，我们将通过语法高亮显示它：

Here’s an example:

```cpp
function test() {
  console.log("notice the blank line before this function?");
}
```

syntax highlighting:

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

###  数学块

您可以使用 **MathJax** 渲染 *LaTeX* 数学表达式。

要添加数学表达式，请输入 `$$` 并按“return”键。这将触发一个接受 *Tex / LaTex* 源的输入字段。例如：

$$
V1×V2=∣ijk∂X∂u∂Y∂u0∂X∂v∂Y∂v0∣\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \\ \frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\ \frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\ \end{vmatrix} V1×V2=∣∣∣∣∣∣i∂u∂X∂v∂Xj∂u∂Y∂v∂Yk00∣∣∣∣∣∣
$$

在 markdown 源文件中，math 块是由一对 ‘$$’ 标记包装的 *LaTeX* 表达式：

```ruby
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$
```

你可以[在这里](https://support.typora.io/Math/)找到更多细节。

###  表

输入`| First Header | Second Header |`并 `return` 按键。这将创建一个包含两列的表。

创建表后，将焦点放在该表上将打开表的工具栏，您可以在其中调整表格的大小，对齐或删除。您还可以使用上下文菜单来复制和添加/删除单个列/行。

表的完整语法如下所述，但没有必要详细了解完整语法，因为表的 markdown 源代码是由 Typora 自动生成的。

在 markdown 源代码中，它们看起来像：

```ruby
| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |
```

您还可以在表格中包含内联 Markdown，例如链接，粗体，斜体或删除线。

最后，通过 `:` 在标题行中包含冒号（），您可以将该列中的文本定义为左对齐，右对齐或居中对齐：

```ruby
| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |
```

最左侧的冒号表示左对齐的列; 最右侧的冒号表示右对齐的列; 两侧的冒号表示中心对齐的列。

###  脚注

```ruby
You can create footnotes like this[^footnote].
[^footnote]: Here is the *text* of the **footnote**.
```

将产生：

你可以像这样创建脚注[1](https://support.typora.io/Markdown-Reference/#fn:footnote)。

将鼠标悬停在“脚注”上标上可查看脚注的内容。

###  横向规则

输入 `***` 或 `---` 在空行上按下 `return` 将绘制一条水平线。

------

###  YAML Front Matter

Typora 现在支持 [YAML Front Matter](https://jekyllrb.com/docs/frontmatter/)。输入 `---` 文章顶部，然后按 `Return` 以引入元数据块。或者，您可以从 Typora 的顶部菜单中插入元数据块。

###  目录（TOC）

输入 `[toc]` 并 `Return` 按键。这将创建一个“目录”部分。TOC 从文档中提取所有标题，并在添加到文档时自动更新其内容。

##  跨度元素

Span 类型将在键入后立即解析和呈现。将光标移动到这些 span 元素的中间会将这些元素扩展为 markdown 源。下面是每个 span 元素的语法说明。

###  链接

Markdown 支持两种链接样式：内联和引用。

在这两种样式中，链接文本由[方括号]分隔。

要创建内联链接，请在链接文本的结束方括号后立即使用一组常规括号。在括号内，将 URL 指向要指向的 URL，以及链接的可选标题，用引号括起来。例如：

```
This is [an example](https://example.com/ "Title") inline link.
[This link](https://example.net/) has no title attribute.
```

将产生：

这是[一个示例](https://example.com/"Title")内联链接。（`<p>This is <a href="http://example.com/" title="Title">`）

[此链接](https://example.net/)没有 title 属性。（`<p><a href="http://example.net/">This link</a> has no`）

####  内部链接

**您可以将href设置为标题**，这将创建一个书签，允许您在单击后跳转到该部分。例如：

命令（在Windows上：Ctrl）+ 单击[此链接](https://support.typora.io/Markdown-Reference/#block-elements)将跳转到标题 `Block Elements`。要查看如何编写，请移动光标或单击该按钮以 `⌘` 按下该键以将元素展开为降价源。

####  参考链接

参考样式链接使用第二组方括号，在其中放置您选择的标签以标识链接：

```ruby
This is [an example][id] reference-style link.

Then, anywhere in the document, you define your link label on a line by itself like this:

[id]: https://example.com/  "Optional Title Here"
```

在 Typora 中，它们将被渲染为：

这是[一个示例](https://example.com/)参考样式链接。

隐式链接名称快捷方式允许您省略链接的名称，在这种情况下，链接文本本身将用作名称。只需使用一组空的方括号 - 例如，将“Google”一词链接到 [google.com](http://google.com) 网站，您只需编写：

```ruby
[Google][]
And then define the link:

[Google]: https://google.com/
```

在 Typora 中，单击该链接将展开它以进行编辑，并且命令 + 单击将在 Web 浏览器中打开超链接。

###  网址

Typora 允许您将URL作为链接插入，用`<`括号括起来`>`。

`<i@typora.io>` 成为 [i@typora.io](mailto:i@typora.io)。

Typora 还会自动链接标准网址。例如：[www.google.com](http://www.google.com)。

###  图片

图像具有与链接类似的语法，但它们 `!` 在链接开始之前需要额外的字符。插入图像的语法如下所示：

```ruby
![Alt text](/path/to/img.jpg)
![Alt text](/path/to/img.jpg "Optional title")
```

您可以使用拖放操作从图像文件或 Web 浏览器插入图像。您可以通过单击图像来修改降价源代码。如果使用拖放操作添加的图像与您当前正在编辑的文档位于同一目录或子目录中，则将使用相对路径。

如果您使用 markdown 构建网站，则可以在本地计算机上 `typora-root-url` 为 YAML Front Matters 中的属性指定图像预览的 URL 前缀。例如，`typora-root-url:/User/Abner/Website/typora.io/` 在 YAML Front Matters 中输入，然后 `![alt](/blog/img/test.png)` 将 `![alt](file:///User/Abner/Website/typora.io/blog/img/test.png)`在 Typora 中处理。

[![拖放图像](https://typora.io/img/drag-img.gif)](https://typora.io/img/drag-img.gif)

[拖放图像](https://typora.io/img/drag-img.gif)



###  重点

Markdown 将星号（`*`）和下划线（`_`）视为重点的指标。用一个包装的文本`*`或`_`将用 HTML `<em>` 标签包装的文本。例如：

```ruby
*single asterisks*
_single underscores_
```

输出：

*单个星号*

*单下划线*

GFM将忽略单词中的下划线，这通常用于代码和名称，如下所示：

> wow_great_stuff
>
> do_this_and_do_that_and_another_thing。

要在其它方式用作强调分隔符的位置生成文字星号或下划线，可以反斜杠转义：

```ruby
\*this text is surrounded by literal asterisks\*
```

Typora 建议使用该 `*` 符号。

###  强大

一个 double `*` 或 `_` 将导致其包含的内容用 HTML `<strong>` 标记包装，例如：

```ruby
**double asterisks**
__double underscores__
```

输出：

**双星号**

**双下划线**

Typora 建议使用该 `**` 符号。

###  码

要指示代码的内联跨度，请使用反引号（`）进行包装。与预格式化的代码块不同，代码跨度表示正常段落中的代码。例如：

```ruby
Use the `printf()` function.
```

将产生：

使用该 `printf()` 功能。

###  删除线

GFM 添加语法来创建删除线文本，标准 Markdown 中缺少该文本。

`~~Mistaken text.~~` 变 错误的文字。

~~Mistaken text.~~

###  下划线

下划线由原始 HTML 提供支持。

`<u>Underline</u>`成为下划线。

<u>Underline</u>

###  表情符号：开心：

使用语法输入表情符号`:smile:`。

😄

用户可以通过 `ESC` 按键触发表情符号的自动完成建议，或者在首选项面板上启用后自动触发表情符号。此外，在菜单栏中转到 `Edit`- > 也可以直接输入 UTF-8 表情符号字符 `Emoji & Symbols`。

###  内联数学

要使用此功能，请先在 `Preference` 面板 - > `Markdown`选项卡中启用它。然后，用于 `$` 包装 TeX 命令。例如：`$\lim_{x \to \infty} \exp(-x) = 0$`将呈现为 LaTeX 命令。

要触发内联数学的内联预览：输入“$”，然后 `ESC` 按键，然后输入 TeX 命令。

$\lim_{x \to \infty} \exp(-x) = 0$

你可以[在这里](https://support.typora.io/Math/)找到更多细节。

###  标

要使用此功能，请先在 `Preference` 面板 - > `Markdown`选项卡中启用它。然后，用于 `~` 包装下标内容。例如：`H~2~O`，`X~long\ text~`/

H~2~O，X~long\ text~/

###  标

要使用此功能，请先在 `Preference` 面板 - > `Markdown`选项卡中启用它。然后，`^` 用来包装上标内容。例如：`X^2^`。

X^2^

###  突出

要使用此功能，请先在 `Preference` 面板 - > `Markdown`选项卡中启用它。然后，用于 `==` 包装高亮内容。例如：`==highlight==`。

==highlight==

##  HTML

您可以使用 HTML 来设置纯 Markdown 不支持的内容。例如，用于 `<span style="color:red">this text is red</span>` 添加红色文本。

<span style="color:red">this text is red</span>

###  嵌入内容

有些网站提供基于 iframe 的嵌入代码，您也可以将其粘贴到 Typora 中。例如：

```ruby
<iframe height='265' scrolling='no' title='Fancy Animated SVG Menu' src='http://codepen.io/jeangontijo/embed/OxVywj/?height=265&theme-id=0&default-tab=css,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'></iframe>
```

<iframe height="265" scrolling="no" title="Fancy Animated SVG Menu" src="https://codepen.io/jeangontijo/embed/OxVywj/?height=265&amp;theme-id=0&amp;default-tab=css,result&amp;embed-version=2" frameborder="no" allowtransparency="true" allowfullscreen="true" style="width: 100%;"></iframe>

###  视频

您可以使用 `<video>`HTML 标记嵌入视频。例如：

```ruby
<video src="xxx.mp4" />
```

###  其他 HTML 支持

你可以[在这里](https://support.typora.io/HTML/)找到更多细节。

1. 这里是*文本*的的**注脚**。
