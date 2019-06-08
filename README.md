# 介绍

本项目致力于对 Python 学习路上的分享

希望各位 Python 爱好者能参与其中，一起探索 Python 魔法背后的奥秘！

# 使用

您可以直接访问 [在线版](https://hubhack.cn/python-book/)，或者根据以下步骤访问本地版。

## 前置条件

您的系统上需要安装好 node。

## 使用 make 命令

若您可使用 make 命令，简单执行如下命令进行初始化：

```console
make init
```

执行如下命令运行服务端：

```console
make run
```

## 使用 gitbook 命令

若您不能使用 make 命令，或想直接使用 gitbook 命令，执行如下命令进行初始化：

```console
npm i -g gitbook-cli #可能需要sudo
gitbook install
```

执行如下命令运行服务端：

```console
gitbook serve
```

## 访问

直接访问 http://localhost:4000 即可查看本书内容。

# Roadmap

大体按照《Python 源码剖析》中的目录结构进行编写。依次介绍 Python 源码基本信息、内建对象和虚拟机。

- [x] 章节
  - [x] 序章
  - [x] 前言
  - [x] Python 源代码的组织
  - [x] Windows 环境下编译 Python
  - [x] UNIX/Linux 环境下编译 Python
  - [x] 修改 Python 源码
- [ ] Python 内建对象
  - [x] Python 对象初探
  - [ ] Python 整数对象
  - [ ] Python 字符串 对象
  - [ ] Python List 对象
  - [x] Python Dict 对象
  - [x] Python Set 对象
 



