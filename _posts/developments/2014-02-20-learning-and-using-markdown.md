---
layout: post
category: 研发
title: Markdown 学习及使用
tags : [Markdown,研发]
image:
  feature: feature.jpg
comments: true
share: true
---

## 概述

本文只是记录学习过程，为了以后使用备忘而已，参考了[Markdown语法说明文档](http://wowubuntu.com/markdown/)。

## 段落、标题、区块代码

一个段落是由一个以上的连接的行句组成，而一个以上的空行则会划分出不同的段落（空行的定义是显示上看起来像是空行，就被视为空行，例如有一行只有空白和 tab，那该行也会被视为空行），一般的段落不需要用空白或换行缩进。
Markdown 支持两种标题的语法，Setext 和 atx 形式。Setext 形式是用底线的形式，利用 `=` （最高阶标题）和 `-` （第二阶标题），Atx 形式在行首插入 1 到 6 个 `#` ，对应到标题 1 到 6 阶。

区块引用则使用 email 形式的 `>` 角括号。

使用一个或多个`空行`分隔内容段来生成段落。

在行末输入2个或以上`空格`再回车来生成换行。

#### Markdown 语法:

    最高阶标题
    ==========

    第二阶标题
    ----------

    ### 3号标题

    #### 4号标题

    >##### 5号标题。
    >
    >使用一个或多个`空行`分隔内容段来生成段落。
    >
    >>在行末输入2个或以上`空格`再回车来生成换行。
    >
    >以上是区块引用文本样例。

#### Markdown 样例:

最高阶标题
==========

第二阶标题
----------

### 3号标题

#### 4号标题

>##### 5号标题。
>
>使用一个或多个`空行`分隔内容段来生成段落。
>
>>在行末输入2个或以上`空格`再回车来生成换行。
>
>以上是区块引用文本样例。

## 分隔线

在一行内使用3个以上的`-`或`_`来建立分隔线，行内除此之外不能有其它内容。

#### Markdown 语法:

    ---
    ___

#### Markdown 样例:

---
___

## 修辞和强调

Markdown 使用`*`来标记需要强调的区段。

#### Markdown 语法:

    使用*星号*来标记需要强调的区段。

    使用**双星号**来标记需要强调的区段。

#### Markdown 样例:

使用*星号*来标记需要强调的区段。

使用**双星号**来标记需要强调的区段。

## 列表

无序列表使用星号、加号和减号来做为列表的项目标记，有序的列表则是使用一般的数字接着一个英文句点作为项目标记。
列表项目标记通常是放在最左边，但是其实也可以缩进，最多 3 个空格，项目标记后面则一定要接着至少一个空格或制表符。
要让列表看起来更漂亮，你可以把内容用固定的缩进整理好。

** 需要注意的是：**

* 列表项目可以包含多个段落，每个项目下的段落都必须缩进 `1个Tab或4个空格` 。
* 如果要在列表项目内放进引用，那 `>` 必须缩进 `1个Tab或4个空格` 。
* 如果要放代码区块的话，该区块就需要缩进两次，也就是必须缩进 `2个Tab或8个空格` 。
* 如果行首出现数字-句点-空白，可以在句点前面加上 `\` 。

#### Markdown 语法:

    ##### 无序列表

    * Candy.
    * Gum.
    * Booze.

    ##### 有序列表

    1. Candy.
    2. Gum.
    3. Booze.

#### Markdown 样例:

##### 无序列表

* Candy.
* Gum.
* Booze.

##### 有序列表

1. Candy.
2. Gum.
3. Booze.

## 链接

Markdown 支援两种形式的链接语法： 行内 和 参考 两种形式，两种都是使用角括号来把文字转成连结。

#### Markdown 语法:

    ##### 行内形式是直接在后面用括号直接接上链接：
    这时一个[样例](http://www.baidu.com/)。

    你也可以选择性的加上 title 属性：
    这时一个[样例](http://www.baidu.com/ "百度")。

    ##### 参考形式可以为链接定一个名称，之后你可以在文件的其他地方定义该链接的内容：
    你喜欢哪个搜索引擎[谷歌][google]还是[百度][baidu]？

    [google]: http://www.google.com/ "谷歌"
    [baidu]: http://www.baidu.com/ "百度"

#### Markdown 样例:

#####行内形式是直接在后面用括号直接接上链接：
这时一个[样例](http://www.baidu.com/)。

你也可以选择性的加上 title 属性：
这时一个[样例](http://www.baidu.com/ "百度")。

#####参考形式可以为链接定一个名称，之后你可以在文件的其他地方定义该链接的内容：
你喜欢哪个搜索引擎[谷歌][google]还是[百度][baidu]？

[google]: http://www.google.com/ "谷歌"
[baidu]: http://www.baidu.com/ "百度"

## 图片

图片的语法和链接很像。

#### Markdown 语法:

    ![汽车左前侧图片](/images/sx4-front-left.jpg "汽车左前侧图片")。

#### Markdown 样例:

![汽车左前侧图片](/res/learning-and-using-markdown/sx4-front-left.jpg "汽车左前侧图片")。

## 代码

在一般的段落文字中，你可以使用 `` ` `` 或使用 `1个Tab或4个空格` 缩进来标记代码区段；

#### Markdown 语法:

    `code example`

#### Markdown 样例:

`code example`

`GitHub Flavored Markdown` 语法支持多个 `` ` `` 开启和结束代码区段可以在代码区域使用 `` ` `` ，开启代码区段 `` ` `` 可以后缀语法单词；

#### Markdown 语法:

    ```text
    code 1
    code 2
    code 3
    ```

#### Markdown 样例:

```text
code 1
code 2
code 3
```

代码区段的起始和结束端都可以放入一个空白，起始端后面一个，结束端前面一个，这样你就可以在区段的一开始就插入反引号；

#### Markdown 语法:

    A single backtick in a code span: `` ` ``

    A backtick-delimited string in a code span: `` `foo` ``

#### Markdown 样例:

A single backtick in a code span: `` ` ``

A backtick-delimited string in a code span: `` `foo` ``

区段内的 `&` `<` `>` 都会被自动的转换成 HTML 实体，这项特性让你可以很容易的在代码区段内插入 HTML 码。

#### Markdown 语法:

    Please don't use any `<blink>` tags.

#### Markdown 样例:

Please don't use any `<blink>` tags.

** 需要注意的是：**

Sublime Text的 `Markdown Preview` 插件生成的HTML代码段

    <pre lang="plain"><code>code example</code></pre>

与CSDN博客支持的HTML代码段

    <pre name="code" class="plain">code example</pre>

显示格式是不一致的，在CSDN博客里直接使用Markdown Preview插件生成的HTML代码段会导致代码格式非常难看。

## 自动链接

Markdown 支持以比较简短的自动链接形式来处理网址和电子邮件信箱，只要是用尖括号包起来，Markdown就会自动把它转成链接。一般网址的链接文字就和链接地址一样。

#### Markdown 语法:

    <http://www.baidu.com>

#### Markdown 样例:

<http://www.baidu.com>

## 反斜杠

Markdown 可以利用反斜杠来插入一些在语法中有其它意义的符号，例如：如果你想要用星号加在文字旁边的方式来做出强调效果（但不用`<em>`标签），你可以在星号的前面加上反斜杠。

    \*literal asterisks\*

##### Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：

    \   反斜线
    `   反引号
    *   星号
    _   底线
    {}  花括号
    []  方括号
    ()  括弧
    #   井字号
    +   加号
    -   减号
    .   英文句点
    !   惊叹号
