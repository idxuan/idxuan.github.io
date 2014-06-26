---
layout: post
category: 工具
title: Git 学习及使用
tags : [Git,研发,源码管理]
image:
    feature: feature.jpg
comments: true
share: true
---

## MSysGit 设置

### 初始化配置：

```bash
#配置ID
git config --global user.name "your_id"
#配置EMAIL
git config --global user.email "your_name@email_address"

# git输出（比如log、status）彩色显示
git config --global color.ui auto

# 全局配置Git不会进行换行符的转换
git config --global core.autocrlf false

# 全局配置文件权限
git config --global core.filemode false
```

### 配置 SSH 证书（下面二选一）：

#### 1. 新建 SSH 证书：

```bash
ssh-keygen -t rsa -C "your_name@email_address"
```

#### 2. 恢复备份 SSH 证书：

1. 建立目录“~/.ssh“；
2. 复制备份的“id_rsa”(私钥) 和“id_rsa.pub”(公钥) 文件至目录“~/.ssh“；

#### 通过 github 测试 SSH 证书：

```bash
ssh -T git@github.com
```

如果看到“You've successfully authenticated, but GitHub does not provide shell access”信息，就表示连接成功。

### 修改或新建 `/etc/fstab`，增加以下内容：

```
d:/UserData/LinuxHome /home
d:/UserData/Tech/Repositories/git /repo
d:/UserData/Work/Projects /projects
d:/UserData/Work/Codes /codes
e:/Downloads /dl
f:/Repositories/git /lrepo
```

### 设置全局配置文件 `/etc/profile`：

```cfg
# 定义语言环境变量
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8

# 定义用户HOME环境变量
#export HOME='/d/Platform/home/BuXing'
export VIM='/usr/share/vim'
export VIMRUNTIME='/usr/share/vim/vim73'
export VIM_OWNS='~/.vim/vimowns'

# 参数 --show-control-chars 正确显示中文
alias ls='ls -hF --color=tty --show-control-chars'                 # classify files in colour
alias dir='ls --color=auto --format=vertical'
alias vdir='ls --color=auto --format=long'
alias ll='ls -l'                              # long list
alias la='ls -A'                              # all but . and ..
alias l='ls -CF'                              #
```

### 右键菜单打开Cygwin在当前目录

#### 1. 增加注册表项：

```registry
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\shell\opengit]
@="打开用 Git Bash"
[HKEY_CLASSES_ROOT\Directory\shell\opengit\command]
@="d:\\GSoft\\Linux32\\MinGW\\git\\git-bash.bat %V"
```

#### 2. 修改Cygwin.bat文件，增加设置路径变量 `set _T=%*`：

```bat
@echo off
set _T=%*
……
```

#### 3. 设置用户配置文件 `\home\${UserName}\.bash_profile`，在最后增加：

```bash
# 右键菜单打开Git在当前目录
export _T=${_T//\\//}   # replace backslash to fowardslash
if [[ $_T == "" ]]; then
export _T=${HOME}
fi
cd "$_T"
```

## Git 常用操作

### 初始化服务仓库

#### 1. 初始化服务仓库，包括工作区，通常为本地仓库

```bash
git init
```

#### 2. 初始化服务仓库，不包括工作区，通常为远程仓库

```bash
git init  --bare
git init  --bare --shared
```

### 增加文件快照到当前工作区

#### 1. 增加所有文件快照到当前工作区

```bash
git add .
```

#### 2. 增加所有文件快照到当前工作区并更新索引为当前文件状态，通常因本地文件未使用Git更新删除。

```bash
git add -A .
```

### 删除文件从当前工作区和索引

```bash
git rm app/user.rb
```

### 重命名文件从当前工作区和索引

```bash
git mv app/oldName.rb app/newName.rb
```

### 提交文件快照到本地仓库

#### 1. 提交到本地仓库，已进行了文件快照

```bash
git commit -m "commit information"
```

#### 2. 提交到本地仓库，未进行了文件快照（仓库已经存在文件）

```bash
git commit -a -m 'commit information'
```

### 查询当前工作区状态

```bash
git status
```

### 查询提交历史

```bash
git log
```

### 获取远程仓库克隆

```bash
git clone ssh://git@github.com/idxuan/GitTest
```

### 增加远程仓库配置

```bash
git remote add github git@github.com:idxuan/GitTest.git (推荐)
git remote add github https://github.com/idxuan/GitTest.git
git remote add local file://f:/Repositories/git/conv_dict
```

### 删除远程仓库配置

```bash
git remote rm github
```

### 远程仓库重命名

```bash
git remote rename oldname newname
```

### 修改远程仓库路径

```bash
git remote set-url github git@github.com:idxuan/GitTest.git
```

### 查询远程仓库配置

```bash
git remote -v
```

### 获取远程仓库

```bash
git pull 远端仓库名 远端分支名:本地分支名
git pull github master
```

### 提交到远程仓库

```bash
git push 远端仓库名 本地分支名:远端分支名
git push github master
git push -u github master
```

### 创建一个没有父节点的分支（github规定，只有该分支中的页面，才会生成网页文件）

```bash
git checkout --orphan gh-pages
```

## GitHub创建步骤

### Create a new repository on the command line

```bash
touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/idxuan/vimim_dict.git
git push -u origin master
```

### Push an existing repository from the command line

```bash
git remote add origin https://github.com/idxuan/vimim_dict.git
git push -u origin master
```

## Git 忽略文件

Git忽略文件有3种设置方式：

### 方式一

在仓库目录下新建一个名为.gitignore的文件（因为是点开头，可能没办法直接在windows目录下直接创建，必须通过右键Git Bash，按照linux的方式来新建.gitignore文件）。
.gitignore文件对其所在的目录及所在目录的全部子目录均有效。通过将.gitignore文件添加到仓库，其他开发者更新该文件到本地仓库，以共享同一套忽略规则。

### 方式二

通过配置.git/info/exclude文件来忽略文件。这种方式对仓库全局有效，只能对自己本地仓库有作用，其他人没办法通过这种方式来共享忽略规则，除非他人也修改其本地仓库的该文件。

### 方式三

通过.git/config配置文件的core. Excludesfile选项，指定一个忽略规则文件（完整路径）。忽略规则在文件中（当然该文件名可以任意取），该方式的作用域是也全局的。

### 忽略样例

```cfg
#忽略掉所有文件名是 foo.txt的文件
foo.txt
#忽略所有生成的 html文件,
*.html
#foo.html是手工维护的，所以例外
!foo.html
#忽略所有.o和 .a文件
*.[oa]
#忽略foo目录
foo/
#忽略所有foo.txt以外文件.
!foo.txt
```

## Git 使用点滴

#### 系统警告：`“LF will be replaced by CRLF”`

##### 原因分析：

各操作系统在文本文件中使用的换行符并不一致，如下：

* `CRLF` 就是回车换行符，一般Windows系统使用；
* `CR` 就是回车符，一般Mac系统使用；
* `LF` 就是换行符，一般Unix/Linux系统使用；

在Windows系统中使用Git来生成一个项目，如果文件中的换行符为 `LF`， 当执行`git add .`时，系统提示：`LF` 将被转换成 `CRLF`。

##### 解决方法：

删除生成的.git文件（删除Git仓库）

```bash
rm -rf .git
```

全局配置Git不会进行换行符的转换

```bash
git config --global core.autocrlf false
```

最后重新执行

```bash
git init
git add .
```

#### 系统错误：`“failed to push some refs to”`

##### 原因分析：

远程仓库中代码版本与本地不一致冲突导致。

##### 解决方法：

1. git pull github master
2. 自动merge或手动merge冲突
3. git push github master

