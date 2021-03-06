---
layout: post
category: 软件
title: Git 学习及使用
tags : [Git,研发,源码管理]
image:
    feature: feature.jpg
comments: true
share: true
---

## 1. 概述

## 2. MSysGit 设置

### 2.1. 初始化配置：

进入 Git Bash，运行下列命令

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

### 2.2. 配置 SSH 证书：

#### 2.2.1. 新建 SSH 证书：

```bash
ssh-keygen -t rsa -C "your_name@email_address"
```

#### 2.2.2. 恢复备份 SSH 证书：

1. 建立目录“~/.ssh“；
2. 复制备份的“id_rsa”(私钥) 和“id_rsa.pub”(公钥) 文件至目录“~/.ssh“；

#### 2.2.3. 通过 github 测试 SSH 证书：

```bash
ssh -T git@github.com
```

如果看到“You've successfully authenticated, but GitHub does not provide shell access”信息，就表示连接成功。

### 2.3. 修改或新建 `/etc/fstab`，增加以下内容：

```
d:/LinuxHome /home
d:/Works/Projects /projects
d:/Works/Codes /codes
e:/Downloads /dl
f:/Repositories/git /local_git
```

### 2.4. 设置全局配置文件 `/etc/profile`：

```cfg
# 定义语言环境变量
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8

# 定义用户HOME环境变量
#export HOME='/d/LinuxHome/xuan'
export VIM='/usr/share/vim'
export VIMRUNTIME='/usr/share/vim/vim74'

# 参数 --show-control-chars 正确显示中文
alias ls='ls -hF --color=tty --show-control-chars'                 # classify files in colour
alias dir='ls --color=auto --format=vertical'
alias vdir='ls --color=auto --format=long'
alias ll='ls -l'                              # long list
alias la='ls -A'                              # all but . and ..
alias l='ls -CF'                              #
```

### 2.5. 右键菜单打开Cygwin在当前目录

#### 2.5.1. 增加注册表项：

```registry
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\shell\opengit]
@="打开用 Git Bash"
[HKEY_CLASSES_ROOT\Directory\shell\opengit\command]
@="d:\\GSoft\\Linux32\\MinGW\\git\\git-bash.bat %V"
```

#### 2.5.2. 修改 `git-bash.bat` 文件，增加设置路径变量 `set _T=%*`：

```bat
@echo off
set _T=%*
……
```

#### 2.5.3. 设置用户配置文件 `\home\${UserName}\.bash_profile`，在最后增加：

```bash
# 右键菜单打开Git在当前目录
export _T=${_T//\\//}   # replace backslash to fowardslash
if [[ $_T == "" ]]; then
export _T=${HOME}
fi
cd "$_T"
```

## 3. Git 常用操作

### 3.1. 初始化服务仓库

#### 3.1.1. 初始化服务仓库，包括工作区，通常为本地仓库

```bash
git init
```

#### 3.1.2. 初始化服务仓库，不包括工作区，通常为远程仓库

```bash
git init  --bare
git init  --bare --shared
```

### 3.2. 增加文件快照到当前工作区

#### 3.2.1. 增加所有文件快照到当前工作区

```bash
git add .
```

#### 3.2.2. 增加所有文件快照到当前工作区并更新索引为当前文件状态，通常因本地文件未使用Git更新删除。

```bash
git add -A .
```

### 3.3. 删除文件从当前工作区和索引

```bash
git rm app/user.rb
```

### 3.4. 重命名文件从当前工作区和索引

```bash
git mv app/oldName.rb app/newName.rb
```

### 3.5. 提交文件快照到本地仓库

#### 3.5.1. 提交到本地仓库，已进行了文件快照

```bash
git commit -m "commit information"
```

#### 3.5.2. 提交到本地仓库，未进行了文件快照（仓库已经存在文件）

```bash
git commit -a -m 'commit information'
```

### 3.6. 查询当前工作区状态

```bash
git status
```

### 3.7. 查询提交历史

```bash
git log
```

### 3.8. 获取远程仓库克隆

#### 3.8.1. 获取远程仓库主库克隆

`git clone` 默认会把远程仓库整个给 `clone` 下来，但只会在本地默认创建一个 `master` 分支。

```bash
git clone ssh://git@github.com/idxuan/GitTest
```

#### 3.8.2. 从远程仓库更新克隆

放弃本地版本，获取远程仓库最新版本

```bash
git reset --hard
git pull
```

注：`git pull` 与 `git fetch` 的区别，`git pull` 相当于 `git fetch && git merge`

在远程仓库已经修改的情况下，本地也已经修改，那么需要通过一些方法避免同步更新错误，例如可以通过指定合并策略来接受远程修改，丢弃本地的所有修改：

```bash
git pull -X theirs
```

其中 -X 指定合并策略是 “theirs" ，就是用别人的覆盖自己的。-s 默认就是 recursive，所以省略了。

#### 3.8.3. 获取远程仓库分支克隆

查看远程分支信息。

```bash
git branch –r
```

查看本地和远程分支信息。

```bash
git branch –a
```

获取远程分支到本地，参数 `-t` 设置为本地当前分支。

```bash
git checkout -t origin/other_branch
```

### 3.9. 增加远程仓库配置

```bash
git remote add github git@github.com:idxuan/GitTest.git (推荐)
git remote add github https://github.com/idxuan/GitTest.git
git remote add local file://f:/Repositories/git/conv_dict
```

### 3.10. 删除远程仓库配置

```bash
git remote rm github
```

### 3.11. 远程仓库重命名

```bash
git remote rename oldname newname
```

### 3.12. 修改远程仓库路径

```bash
git remote set-url github git@github.com:idxuan/GitTest.git
```

### 3.13. 查询远程仓库配置

```bash
git remote -v
```

### 3.14. 获取远程仓库

```bash
git pull 远端仓库名 远端分支名:本地分支名
git pull github master
```

### 3.15. 提交到远程仓库

```bash
git push 远端仓库名 本地分支名:远端分支名
git push github master
git push -u github master
```

### 3.16. 创建一个没有父节点的分支（github规定，只有该分支中的页面，才会生成网页文件）

```bash
git checkout --orphan gh-pages
```

### 3.17. 重置回滚

重置回滚本地

```bash
git reset --hard 版本号
```

重置回滚远程

```bash
git push -f
```

然后每个本地都要执行 `git reset --hard 版本号` 操作。
该方法只适合小的团队或者个人的项目使用，大的团队还是建议 `git reset --hard`版本号，然后比较多所有有变动的文件，然后覆盖回去，然后提交(commit)，然后push的远程。

### 3.18. 强制覆盖本地文件

1. `git fetch` 下载远程最新的，但不尝试或修改任何东西。 然后 `git reset master` 分支重置到刚才。

```bash
git fetch --all
git reset --hard origin/master
```


2. 试试这个。

```bash
git reset --hard HEAD
git pull
```


3. clean -f 如果您有未跟踪目录，还需要-d 选项。

```bash
git reset --hard HEAD
git clean -f -d
git pull
```

## 4. GitHub创建步骤

### 4.1 Create a new repository on the command line

```bash
touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/idxuan/vimim_dict.git
git push -u origin master
```

### 4.2 Push an existing repository from the command line

```bash
git remote add origin https://github.com/idxuan/vimim_dict.git
git push -u origin master
```

## 5. Git 忽略文件

Git忽略文件有3种设置方式：

### 5.1. 方式一

在仓库目录下新建一个名为.gitignore的文件（因为是点开头，可能没办法直接在windows目录下直接创建，必须通过右键Git Bash，按照linux的方式来新建.gitignore文件）。
.gitignore文件对其所在的目录及所在目录的全部子目录均有效。通过将.gitignore文件添加到仓库，其他开发者更新该文件到本地仓库，以共享同一套忽略规则。

### 5.2. 方式二

通过配置.git/info/exclude文件来忽略文件。这种方式对仓库全局有效，只能对自己本地仓库有作用，其他人没办法通过这种方式来共享忽略规则，除非他人也修改其本地仓库的该文件。

### 5.3. 方式三

通过.git/config配置文件的core. Excludesfile选项，指定一个忽略规则文件（完整路径）。忽略规则在文件中（当然该文件名可以任意取），该方式的作用域是也全局的。

### 5.4. 忽略样例

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

## 6. Git Config 配置项

### 6.1 默认远程仓库

```bash
git config branch.master.remote origin
```

## 7. Git 使用点滴

### 7.1 系统警告：`LF will be replaced by CRLF`

**原因分析：**

各操作系统在文本文件中使用的换行符并不一致，如下：

* `CRLF` 就是回车换行符，一般Windows系统使用；
* `CR` 就是回车符，一般Mac系统使用；
* `LF` 就是换行符，一般Unix/Linux系统使用；

在Windows系统中使用Git来生成一个项目，如果文件中的换行符为 `LF`， 当执行`git add .`时，系统提示：`LF` 将被转换成 `CRLF`。

**解决方法：**

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

### 7.2 系统错误：`failed to push some refs to`

**原因分析：**

远程仓库中代码版本与本地不一致冲突导致。

**解决方法：**

1. git pull github master
2. 自动merge或手动merge冲突
3. git push github master

### 7.2 系统错误：`commit your changes or stash them before you can merge`

**原因分析：**

更新本地代码时远程仓库中代码版本与本地不一致冲突导致。

**解决方法：**

#### 7.2.1 放弃本地版本，获取远程仓库最新版本

```bash
git reset --hard
git pull
```

其中 `git reset` 是针对版本,如果想针对文件回退本地修改,使用

```
git checkout HEAD file/to/restore
```

#### 7.2.2 使用 `git stash` 保留生产服务器上所做的改动,仅仅并入新配置项。

```bash
git stash
git pull
git stash pop
```

然后可以使用 `git diff -w +filename` 来确认代码自动合并的情况，并作出相应修改。

* git stash: 备份当前的工作区的内容，从最近的一次提交中读取相关内容，让工作区保证和上次提交的内容一致。同时，将当前的工作区内容保存到 Git 栈中。
* git stash pop: 从 Git 栈中读取最近一次保存的内容，恢复工作区的相关内容。由于可能存在多个 Stash 的内容，所以用栈来管理，pop 会从最近的一个 stash 中读取内容并恢复。
* git stash list: 显示 Git 栈内的所有备份，可以利用这个列表来决定从那个地方恢复。
* git stash clear: 清空 Git 栈。此时使用 gitg 等图形化工具会发现，原来 stash 的哪些节点都消失了。

### 7.3 关于回滚

Git 的历史记录是不可修改的，也就是不能更改任何已经发生的事情。
任何操作都只是在原来的操作上修改。也就是说，即使删除了一个分支，修改了一个提交，或者强制重置，仍然可以回滚这些操作。

样例：

```bash
$ git init
$ touch foo.txt
$ git add foo.txt
$ git commit -m "initial commit"

$ echo 'new data' >> foo.txt
$ git commit -a -m "more stuff added to foo"
```

现在看 Git 的历史记录，可以看到两次提交：

```bash
$ git log
* 98abc5a (HEAD, master) more stuff added to foo
* b7057a9 initial commit
```

现在重置回第一次提交的状态：

```bash
$ git reset --hard b7057a9
$ git log
* b7057a9 (HEAD, master) initial commit
```

这看起来是丢掉了第二次的提交，没有办法找回来了。但是 `reflog` 就是用来解决这个问题的。简单的说，它会记录所有 `HEAD` 的历史，也就是说当做 `reset`，`checkout`等操作的时候，这些操作会被记录在 `reflog` 中。

```bash
$ git reflog
b7057a9 HEAD@{0}: reset: moving to b7057a9
98abc5a HEAD@{1}: commit: more stuff added to foo
b7057a9 HEAD@{2}: commit (initial): initial commit
```

所以要找回第二次 `commit`，只需要做如下操作：

```bash
$ git reset --hard 98abc5a
```

再来看一下 Git 记录：

```bash
$ git log
* 98abc5a (HEAD, master) more stuff added to foo
* b7057a9 initial commit
```

所以如果因为 `reset` 等操作丢失一个提交的时候，总是可以把它找回来。除非操作已经被 Git 当做垃圾处理掉了，一般是30天以后。

### 7.4 Clone 错误 `does not appear to be a git repository`

Clone 用绝对路径，不要使用相对路径
错误：git@ip:gitosis-admin.git
正确：git@ip:/home/git/repositories/gitosis-admin.git