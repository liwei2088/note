# Git教程

## 1 Git简介

### 1.1 Git概念

​	Git是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。Git 与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。

### 1.2 Git安装

​	在使用Git前我们需要先安装 Git。Git 目前支持 Linux/Unix、Solaris、Mac和 Windows 平台上运行。

Git 各平台安装包下载地址为：[http://git-scm.com/downloads](http://git-scm.com/downloads)

#### 1.2.1 Linux 平台上安装

​	Git 的工作需要调用 curl，zlib，openssl，expat，libiconv 等库的代码，所以需要先安装这些依赖工具。

在有 yum 的系统上（比如 Fedora）或者有 apt-get 的系统上（比如 Debian 体系），可以用下面的命令安装：

各 Linux 系统可以很简单多使用其安装包管理工具进行安装：

##### 1.2.1.1 Debian / Ubuntu

Debian/Ubuntu Git 安装命令为：

```bash
$ apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev

$ apt-get install git

$ git --version
git version 2.18.0
```

##### 1.2.1.2 Centos / RedHat

如果你使用的系统是 Centos/RedHat 安装命令为：

```bash
$ yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel

$ yum -y install git-core

$ git --version
git version 2.18.0
```

#### 1.2.2  Windows 平台上安装

​	在Windows上使用Git，可以从Git官网直接[下载安装程序](https://git-scm.com/downloads)，然后按默认选项安装即可。

![git官网](E:\(06)note\git\images\01.png)

安装完成后，在开始菜单里找到"Git"->"Git Bash"，会弹出 Git 命令窗口，你可以在该窗口进行 Git 操作。

![bash](E:\(06)note\git\images\02.png)

#### 1.2.3  Mac 平台上安装

​	在Mac上使用Git，也可以从Git官网直接[下载安装程序](https://git-scm.com/downloads)，然后按默认选项安装即可。

### 1.3 Git基础配置

​	Git 提供了一个叫做 git config 的工具，专门用来配置或读取相应的工作环境变量。这些环境变量，决定了 Git 在各个环节的具体工作方式和行为。

#### 1.3.1  配置用户

​	配置个人的用户名称和电子邮件地址：

```bash
$ git config --global user.name "liwei2088"				#配置用户名
$ git config --global user.email "liwei2088@sohu.com"	#配置邮箱
$ git config --global color.ui auto						#配置颜色显示 windows系统不用配置
```

​	如果用了 **--global** 选项，那么更改的配置文件就是位于你用户主目录下的那个，以后你所有的项目都会默认使用这里配置的用户信息。

#### 1.3.2 查看配置

要检查已有的配置信息，可以使用 git config --list 命令：

```bash
$ git config --list		#查看全部配置信息
$ git config user.name	#查看某一配置信息
```

## 2. Git 工作流程

### 2.1 基本流程

一般工作流程如下：

- 从远程版本库获取最新代码资源；

- 系统开发，编写代码（新增、修改或删除代码资源）；

- 提交代码给Git本地版本库；

- 最终将本地版本库提交到远程版本库，分享代码给团队其他成员；

> 注意：在整个过程如果发现错误，可以撤回提交并再次修改并提交。

### 2.2 工作区、暂存区和版本库的概念

先来理解下Git 工作区、暂存区和版本库概念

- **工作区：**就是你在电脑里能看到的目录。
- **暂存区：**英文叫stage, 或index。一般存放在 ".git目录下" 下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引区（index）。
- **版本库：**工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
  - 本地库：local 指的是本机上的版本库。
  - 远程库：remote 指远端服务器上的版本库，如GitHub。

下面这个图展示了工作区、版本库中的暂存区和版本库之间的关系：

![工作区、索引区和版本库关系](E:\(06)note\git\images\1352126739_7909.jpg)

## 3 Git 创建仓库



