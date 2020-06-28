---
title: React高级——生命周期改善程序性能
date: 2020-06-28 15:21:25
tags:
categories: react
---

首先你要确认你安装了`React Developer Tools` 有了这个浏览器插件，就可以在控制台中找到React标签，然后在右边点开设置，选中`highlight Updates`。

![image-20200628160640699](/Users/zhaohui/Library/Application Support/typora-user-images/image-20200628160640699.png)

这时候你在浏览器的文本框中输入一下内容，你可以清楚的看到子组件也发生了重新`render`的情况。

有很多程序员会忽略这样的性能损耗，认为没有什么大不了的，但是软件的卡顿是一点点产生的，所以必须要减少性能损耗。

这时我们可以用`shouldComponentUpdate`解决

这个问题看似很小，但是当你页面很复杂时，足以影响用户体验。其实用`shouldComponentUpdate`函数就可以简单的解决调这个问题。

![image-20200628161020272](/Users/zhaohui/Library/Application Support/typora-user-images/image-20200628161020272.png)

现在的代码就优雅一些了，也不那么暴力了。这就算是完美解决了子组件的渲染性能问题，你写的代码质量也得到了提高。