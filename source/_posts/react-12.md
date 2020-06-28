---
title: React进阶——单项数据流和其他
date: 2020-05-30 13:05:59
tags:
categories: react
---

### React 单项数据流

React是单项数据流，数据流主要从父节点传递到子节点（通过props）

如果顶层（父级）的某个props改变了，React会重渲染所有的子节点

### Props：

 `props`是property的缩写，可以理解为HTML标签的attribute。

　　不可以使用`this.props`直接修改props，因为`props是`只读的，`props`是用于整个组件树中传递数据和配置。

　　在当前组件访问`props`，使用`this.props`。

### State：

​		每个组件都有属于自己的`state`，`state`和`props`的区别在于前者(state)只存在于组件内部，只能从当前组件调用`this.setState`修改state值（不可以直接修改`this.state！`）。

　　一般我们更新子组件都是通过改变`state`值，将state值通过属性传递给子组件，子组件的获取`props`值从而达到更新。

### 函数式编程

1. 函数式编程让我们的代码更清晰，每个功能都是一个函数。
2. 函数式编程为我们的代码测试代理了极大的方便，更容易实现前端自动化测试。

