---
title: React开发环境搭建
date: 2020-05-26 14:00:25
tags:
categories: react
---

### 安装Node.js

使用`React.js`是可以用最原始的``标签进行引入的工作中也不会有这种形式进行引入。所以就采用脚手架形式的安装。这就需要先安装`Node.js`，用里边的`npm`来进行安装。

Node中文网址：[http://nodejs.cn/](http://nodejs.cn/)

Node.js` 安装好以后，如果是Windows系统，可以使用 `Win+R`打开运行，然后输入`cmd`，打开终端（或者叫命令行工具）

```
node -v
```

如果正确出现版本号，说明Node安装成功了

然后再输入代码:

```
npm -v
```

如果正确出现版本号，说明npm也是没问题的，这时候`Node.js`安装就算完成了。

### 脚手架的安装

Node安装好之后，你就可以使用npm命令来安装脚手架工具了，方法很简单，只要打开终端，然后输入下面的命令就可以了。

```
npm install -g create-react-app
```

创建第一个React项目

