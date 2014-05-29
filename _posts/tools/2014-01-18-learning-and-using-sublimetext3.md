---
layout: post
category: 工具
title: Sublime Text3 学习及使用
tags : [Sublime,文本编辑]
image:
  feature: feature.jpg
comments: true
share: true
---


一直是Vim的用户，对于文本编辑来说确实无可挑剔。可是因为团队开发不可避免的也会使用别的一些IDE工具，相信会有很多Vim的爱好者会和我有同样的烦恼，在IDE里很顺手的按下快捷键，输出字符了，按ESC，再按命令，又输出字符了，再再按ESC……无语啊！

因为Vim的命令编辑模式的特殊性，大多数的IDE都无法配置自定义的Vim快捷键，最多是些标准的“hjkl”等。而且在日常工作中经常会和别人交流，用Vim确实太小众了，想想看，敏捷开发结对时，你用Vim，旁边坐着的哥们是纯Windowser……

终于下定决心，再学习一种文本编辑器，网上逛了一圈，选了Sulime Text。写下这篇文章，记录了学习的过程，后期会尽力不断更新修正……

---

快捷键查阅了Sublime Text3的keymap文件，实际试用后编写，Sublime Text2可能会有少许差异。

配置文件中字体是我在网上找到的“雅黑+Consolas”编程字体，自己修改了一些不喜欢的地方，见下图。你可以变更配置文件为自己喜欢的或直接注释即可。

![Sublime Text3字体图片](/res/2014-01-18-learning-and-using-sublimetext3/sublime-text3-full-screen.jpg "Sublime Text3字体图片")


1. Sublime Text 快捷键
-----------------------

### 1.1. 文件窗口面板

* **Ctrl+Shift+P**: 打开命令面板
* **Ctrl+Alt+P**: 打开项目切换面板
* **Ctrl+P**: 打开文件切换面板
* **Ctrl+`**: 打开控制台
* **Ctrl+N**: 新建文件
* **Ctrl+Shift+N**: 新建窗口
* **Ctrl+Shift+T**: 打开最后关闭的文件
* **Ctrl+O**: 打开文件
* **Ctrl+S**: 保存文件
* ***Ctrl+Shift+S**: 另存文件（建议：保存所有文件）
* **Ctrl+W**: 关闭文件
* ***Ctrl+Shift+W**: 关闭窗口（建议：关闭所有文件）
* **Ctrl+K,Ctrl+B**: 开关侧栏
* **F11**: 全屏
* **Shift+F11**: 全屏免打扰模式（只显示当前编辑文件）
* **Alt+Shift+Num**: 分屏显示共Num个窗口
* **Alt+Num**: 切换第Num个索引（默认文件）
* **Ctrl+Tab**: 按文件浏览顺序切换文件
* **Ctrl+[PageUp,PageDown]**: 切换上/下个文件
* **Ctrl+K,Ctrl+Up**: 当前文件至分割窗口
* **Ctrl+K,Ctrl+Shift+Up**: 新建文件至分割窗口
* **Ctrl+K,Ctrl+Down**: 合并分割窗口
* **Ctrl+K,Ctrl+[Left,Right]**: 焦点移动到上/下个窗口
* **Ctrl+K,Ctrl+Shift+[Left,Right]**: 当前文件移动到上/下个窗口

### 1.2. 移动定位

* **Ctrl+P,#或Ctrl+;**: 定位关键词
* **Ctrl+P,:或Ctrl+G**: 定位行
* **Ctrl+P,@或Ctrl+R**: 定位函数
* **Ctrl+Shift+R**: 定位函数从项目
* **[Home,End]**: 行首/行尾
* **Ctrl+[Home,End]**: 页首/页尾
* **Ctrl+M**: 跳转至对应的括号
* **Ctrl+[Left,Right]**: 跳转至上/下一个词
* **Alt+[Left,Right]**: 跳转至上/下一个子词（区分大小写）
* **Alt+-**: 跳转至上一个光标位置
* **Alt+Shift+-**: 跳转至下一个光标位置
* **Ctrl+[Up,Down]**: 屏幕按行上/下滚动

### 1.3. 选择

* **Shift+[Home,End]**: 选择到行首行尾
* **Ctrl+Shift+[Home,End]**: 选择到页首页尾
* **Ctrl+Shift+J**: 选择当前缩进内容
* **Ctrl+Shift+M**: 选择括号内的内容（重复选择括号）
* **Alt+F3**: 选择所有相同的词
* **Ctrl+D**: 选择词 (重复按下多重选择可同步修改)
* **Ctrl+K,Ctrl+D**: 跳过当前选择词
* **Ctrl+Shift+[Left,Right]**: 选择并跳转至上/下一个词
* **Alt+Shift+[Left,Right]**: 选择并跳转至上/下一个子词（区分大小写）
* **Ctrl+L**: 选择行（重复按下将下一行加入选择）

### 1.4. 编辑

* **Ctrl+Z**: 恢复
* ***Ctrl+Shift+Z**: 重做（建议：Ctrl+Alt+Z）
* **Ctrl+Y**: 重做或重复
* **Ctrl+U**: 软撤销（可撤销光标移动）
* **Ctrl+Shift+U**: 软重做（可重做光标移动）
* **Ctrl+C或Ctrl+Insert**: 复制
* **Ctrl+X或Shift+Delete**: 剪切
* **Ctrl+V或Shift+Insert**: 粘贴
* **Ctrl+Shift+V**: 粘贴并格式化
* **Ctrl+K,Ctrl+V**: 粘贴从历史记录
* **Tab**: 光标后缩进
* **Shift+Tab**: 行首反缩进
* **Ctrl+]**: 行缩进
* **Ctrl+[**: 行反缩进
* **Ctrl+J**: 合并行
* **Alt+Q**: 自动换行
* **F9**: 行排序（大小写不敏感）
* **Ctrl+F9**: 行排序（大小写敏感）
* **Ctrl+Shift+D**: 复制行（如果已经选择词，则复制此词）
* **Ctrl+Shift+[Up,Down]**: 移动光标所在行与上/下行互换
* **Ctrl+Enter**: 在当前行后插入新行
* **Ctrl+Shift+Enter**: 在当前行前插入新行
* **Ctrl+Shift+K**: 删除光标所在行
* **Ctrl+K,Ctrl+K**: 从光标处删除至行尾
* **Ctrl+K,Ctrl+Backspace**: 从光标处删除至行首
* **Ctrl+T**: 选中词互换（选择后按Ctrl增加选择区）
* **Ctrl+K,Ctrl+U**: 词改为大写
* **Ctrl+K,Ctrl+L**: 词改为小写

### 1.5. 查找/替换

* **Ctrl+F**: 查找
* **Ctrl+H**: 查找替换
* **Ctrl+Shift+F**: 查找或替换，可选文件夹或过滤器
* ***Ctrl+I**: 累加查找（建议：Alt+I）
* **F3**: 查找下一个
* **Shift+F3**: 查找上一个

### 1.6. 列模式

* **鼠标中键或Shift+鼠标右键**: 列模式
* **Ctrl+鼠标列模式**: 增加列选择
* **Alt+鼠标列模式**: 减少列选择
* **Ctrl+Alt+[Up,Down]**: 选择上/下多行列模式，光标在当前列
* **Ctrl+Shift+L**: 选区进入列模式，光标在行尾

### 1.7. 书签

* **Ctrl+F2**: 添加/删除书签
* **F2**: 下一个书签
* **Shift+F2**: 前一个书签
* **Alt+F2**: 选择所有书签
* **Ctrl+Shift+F2**: 删除所有书签

### 1.8. 标记

* ***Ctrl+K, Ctrl+Space**: 设置标记（建议：Alt+;,Alt+Space）
* ***Ctrl+K, Ctrl+A**: 从光标位置选择至标记（建议：Alt+;,Alt+A）
* ***Ctrl+K, Ctrl+W**: 从光标位置删除至标记（建议：Alt+;,Alt+W）
* ***Ctrl+K, Ctrl+X**: 光标位置交换标记（建议：Alt+;,Alt+X）
* ***Ctrl+K, Ctrl+G**: 清除标记（建议：Alt+;,Alt+G）

### 1.9. 代码

* ***Ctrl+Space**: 自动完成，重复选择下一提示（建议：Alt+Space）
* **Ctrl+/**: 行注释
* **Ctrl+Shift+/**: 块注释
* **Ctrl+Shift+[**: 折叠当前
* **Ctrl+Shift+]**: 展开当前
* **Ctrl+K,Ctrl+T**: 折叠属性
* **Ctrl+K,Ctrl+Num**: 折叠Num层级
* **Ctrl+K,Ctrl+0**: 展开所有
* **Ctrl+B或F7**: 构建
* **Ctrl+Shift+B**: 运行
* **Ctrl+Break**: 执行

### 1.10. XML/HTML

* **Ctrl+Shift+A**: 选择标签内的内容
* **Ctrl+Shift+.**: 闭合当前标签

### 1.11. 宏

* **Ctrl+Q**: 开关宏记录
* ***Ctrl+Shift+Q**: 运行宏（建议：Ctrl+Alt+Q）

### 1.12. 拼写检查

* **F6**: 开启/关闭拼写检查
* **Ctrl+F6**: 定位下一个拼错
* **Ctrl+Shift+F6**: 定位上一个拼错

### 1.13. 自定义快捷键

* ***Alt+[H,J,K,L]**: 上下左右移动
* ***Alt+Shift+[H,J,K,L]**: 上下左右移动并选择
* ***Ctrl+Alt+[J,K]**: 屏幕按行上/下滚动
* ***Ctrl+Alt+[H,L]**: 左右移动至上/下一个词
* ***Ctrl+Alt+Shift+[H,L]**: 左右移动至上/下一个词并选择
* ***Ctrl+=**: 格式化选择行
* ***Alt+;,Alt+B**: 转换HTML代码段到CSDN博客格式（ToCsdnBlog）

### 1.14. 插件"BracketHighlighter"常用快捷键

原快捷键前缀ctrl+alt+super修改为ctrl+alt+shift

* ***Ctrl+Alt+Shift+[Up, Down]**: 移动到左/右括号
* ***Ctrl+Alt+Shift+[Left,Right]**: 如果光标紧贴属性或在属性字符串内，直接选择此属性，否则选择光标左/右侧属性
* ***Ctrl+Alt+Shift+S**: 选择括号内容
* ***Ctrl+Alt+Shift+T**: 从HTML/XML标签选择标签名称

### 1.15. 插件"TrailingSpacer"常用快捷键

原快捷键前缀ctrl+shift修改为ctrl+alt

* ***Ctrl+Alt+T**: 开关显示多余空格
* ***Ctrl+Alt+D**: 删除多余空格

### 1.16. 插件"DeleteBlankLines"常用快捷键

* **Ctrl+Alt+Backspace**: 删除选择区域所有空行
* **Ctrl+Alt+Shift+Backspace**: 删除选择区域多余空行

### 1.17. 插件"ConvertToUTF8"常用快捷键

* **Ctrl+Shift+C**: 转换文件到GBK
* ***Ctrl+Shift+G**: 转换文件到UTF-8

### 1.18. 插件"Alignment"常用快捷键

* **Ctrl+Alt+A**: 以定义的符号（默认等号）为准格式化

### 1.19. 插件"Tag"常用快捷键

* **Ctrl+Alt+F**:  格式化

### 1.20. 插件"SublimeTmpl"常用快捷键

* ***Ctrl+Alt+Shift+J**: 新建Java模板文件
* ***Ctrl+Alt+Shift+G**: 新建Go模板文件
* ***Ctrl+Alt+Shift+Y**: 新建Python模板文件
* ***Ctrl+Alt+Shift+M**: 新建Markdown模板文件


### 1.21. 插件"InsertNums"常用快捷键

* **Ctrl+Alt+N**: 插入序号

**注意**：

* `[A,B,C]` 表示A,B,C可选其一；
* `Num` 表示阿拉伯数字;
* `*` 表示自定义快捷键或不符合日常习惯建议修改。

2. Sublime Text 插件安装方式
----------------------------

### 2.1.直接安装

安装Sublime text 2插件很方便，可以直接下载安装包解压缩到Packages目录（Data\Packages）。或在程序里直接打开，菜单选择“Preferences”-> “Browse Packages...”。

如果安装了Git工具，如“MSysGit”等，也可以直接在Packages目录下运行“git clone...”完成安装。

### 2.2.使用Package Control安装

安装“Package Control组件”，然后按下Ctrl+Shift+P调出命令面板，输入“Package Control:Install Package”，然后在列表中选中要安装的插件。

### 2.3.使用Github的repository安装

按下Ctrl+Shift+P调出命令面板，输入“Package Control:Add Repository”，输入一个插件的Github地址，然后再次按下Ctrl+Shift+P调出命令面板，输入“Package Control:Install Package”，现在就可以安装刚刚添加的Repository里面的插件了。

3. Sublime Text 使用点滴
------------------------

### Sublime Text 快捷键设置

菜单选择“Preferences”->“Key Bindings-User” ，粘贴并修改为你自己习惯的即可。

###Sublime Text 参数配置

菜单选择“Preferences”->“Settings-User”，粘贴并修改为你自己习惯的即可。

### 空格和Tab转换

按下Ctrl+Shift+P调出命令面板，输入“Convert Indentation to Tabs”将空格转换为Tab。

如果安装了“LineEndings”插件，可以将当前文件或所有打开文件进行空格和Tab互转。通过按下Ctrl+Shift+P调出命令面板，或选择右下方状态栏菜单操作。

### 修改系统或插件默认的设置或快捷键

有时候我们想修改系统或插件默认的设置或快捷键，但从“Sublime Text”程序里打开默认是不允许修改的，怎么办呢？

1. 在“Data/Packages/”用户目录下新建或编辑配置文件；
2. 直接修改原配置文件，解压缩编辑后重新压缩即可。

    系统配置文件在“Packages”目录下“Default.sublime-package”文件解压缩，修改后重新压缩既可。
    插件配置文件在“Data/Packages/”用户包目录下或在Data/Installed Packages/”安装包文件。同上，直接修改或解压缩，修改后重新压缩既可。

### Bug

1. 使用“SublimeTmpl”新建文件模板插件如果把所有文件都关闭，焦点不在主窗口的话，“SublimeTmpl”菜单变灰，无法使用。
2. 不知道是“Sublime Text3”还是“ConvertToUTF8 ”的问题，如果在Windows系统里更改了“DPI“显示比例的话，标签页和侧边栏中文字体会变成方框乱码，感觉好像放不下一样。

### Java编译运行

#### 1. 增加编译运行批处理文件“runJava.bat”并放入可执行路径，脚本内容如下：

    {% highlight bat %}
    @ECHO OFF

    cd %~dp1
    ECHO Compiling %~nx1.......
    IF EXIST %~n1.class (
        DEL %~n1.class
    )
    javac -encoding utf-8 %~nx1
    IF EXIST %~n1.class (
        ECHO -----------OUTPUT-----------
        java %~n1
    )
    {% endhighlight %}

注：“javac -encoding utf-8 %~nx1”的意义是指定源文件是“UTF-8”格式，如果你的源文件是其他格式，请修改或删除“-encoding utf-8”。

#### 2. 将“Packages”目录下“Java.sublime-package”文件解压缩，修改“JavaC.sublime-build”文件后重新压缩，修改内容如下：

    {% highlight text %}
    {
        "shell_cmd": "runJava.bat \"$file\"",
        "file_regex": "^(...*?):([0-9]*):?([0-9]*)",
        "selector": "source.java",
        "encoding": "gbk"
    }
    {% endhighlight %}

注：第一行的“runJava.bat”即上面的脚本文件，最后一行"encoding": "gbk"的意义是将输出编码定义为本地中文代码页。如果你编译运行其他程序是发生“[Decode error - output not utf-8]”错误，都可以用此方法解决问题。

4. 本文相关下载资源
-------------------

* [下载我的快捷键设置](/res/2014-01-18-learning-and-using-sublimetext3/Default\ (Windows\).sublime-keymap "我的快捷键设置")。
* [下载我的参数配置](/res/2014-01-18-learning-and-using-sublimetext3/Preferences.sublime-settings "我的参数配置")。
* [下载我的CSDN Blog插件](https://github.com/idxuanjun/ToCsdnBlog "我的CSDN Blog插件")。
因为我是用Markdown写的CSDN博客，但“Markdown Preview”插件生成的HTML代码段与CSDN博客支持的格式不一致，所以自己写了个插件转换一下。
* [下载Package Control组件](https://sublime.wbond.net/installation "Package Control组件安装下载")
