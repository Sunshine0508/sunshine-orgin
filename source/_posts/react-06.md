---
title: React中jsx语法简介
date: 2020-05-27 15:01:47
tags:
categories: react
---

### JSX简介

> JSX就是Javascript和XML结合的一种格式。React发明了JSX，可以方便的利用HTML语法来创建虚拟DOM，当遇到`<`，JSX就当作HTML解析，遇到`{`就当JavaScript解析.

比如我们写一段JSX语法

```
<ul className="my-list">
    <li>JSPang.com</li>
    <li>I love React</li>
</ul>
```

比如我们以前写一段JS代码：

```
var child1 = React.createElement('li', null, 'JSPang.com');
var child2 = React.createElement('li', null, 'I love React');
var root = React.createElement('ul', { className: 'my-list' }, child1, child2);
```

从代码量上就可以看出JSX语法大量简化了我们的工作。

### 组件和普通JSX语法区别

这个说起来也只有简单的一句话，就是你自定义的组件必须首写字母要进行大写，而JSX是小写字母开头的。

### JSX使用三元运算符

在JSX中也是可以使用js语法的，我们先简单讲解一个三元元算符的方法。

```
import React from 'react'
const Component = React.Component


class App extends Component{
    render(){
        return (
            <ul className="my-list">
                <li>{false?'zhaohui58.cn':'Sunshine'}</li>
                <li>I love React</li>
            </ul>
        )
    }
}

export default App;
```

总结：作为一个初学者对JSX有一个简单的了解