---
title: React进阶——JSX踩坑的几个地方
date: 2020-05-27 16:28:49
tags:
categories: react
---

### JSX代码注释

`JSX`中的代码注释是非常有讲究的，这个书上介绍的也非常少，所以在这里讲一下，因为在初学`React`在这里踩过坑。

第一次写`JSX`注释，是直接这样写的，当然这样写是完全不对的。

```
<Fragment>
    //第一次写注释，这个是错误的
    <div>
        <input value={this.state.inputValue} onChange={this.inputChange.bind(this)} />
        <button onClick={this.addList.bind(this)}> 增加项目 </button>
    </div>
```

那写`JSX`的注释，可以有下面两种写法:

```
<Fragment>
    {/* 正确注释的写法 */}
    <div>
        <input value={this.state.inputValue} onChange={this.inputChange.bind(this)} />
        <button onClick={this.addList.bind(this)}> 增加项目 </button>
    </div>
```

如果你记不住，有个简单的方法，就是用`VSCode`的快捷键，直接按`Ctrl+/`，就会自动生成正确的注释了。

你可以把这个理解为，在jsx中写javascript代码。所以外出我们套入了`{}`，然后里边就是一个多行的javascript注释。如果你要使用单行祝注释`//`，你需要把代码写成下面这样。

```
<Fragment>
    {
        //正确注释的写法 
    }
    <div>
        <input value={this.state.inputValue} onChange={this.inputChange.bind(this)} />
        <button onClick={this.addList.bind(this)}> 增加项目 </button>
    </div>
```

也就是你要进行换行，所以个人认为这种方法不太优雅，所以推荐第一种注释方法。

### JSX中的class陷阱

react中要把`class`换成`className`，它是防止和`js`中的`class`类名 冲突，所以要求换掉。这也算是一个小坑吧。

### JSX中的html解析问题

如果想在文本框里输入一个``标签，并进行渲染。默认是不会生效的，只会把``标签打印到页面上，这并不是我想要的。如果工作中有这种需求，可以使用`dangerouslySetInnerHTML`属性解决。具体代码如下：

```
<ul>
    {
        this.state.list.map((item,index)=>{
            return (
                <li 
                    key={index+item}
                    onClick={this.deleteItem.bind(this,index)}
                    dangerouslySetInnerHTML={{__html:item}}
                >
                </li>
            )
        })
    }
</ul> 
```

上面的代码就可以实现`html`格式的输出。

JSX中label标签的坑

JSX中``的坑，也算是比较大的一个坑，label是`html`中的一个辅助标签，也是非常有用的一个标签。

先看下面的代码，我们在文本框前面加入一个``。

```
<div>
    <label>加入项目：</label>
    <input className="input" value={this.state.inputValue} onChange={this.inputChange.bind(this)} />
    <button onClick={this.addList.bind(this)}> 增加项目 </button>
</div>
```

这时候想点击“加入项目”直接可以激活文本框，方便输入。按照`html`的原思想，是直接加ID就可以了。代码如下：

```
<div>
    <label for="Sunshine">加入项目：</label>
    <input id="Sunshine" className="input" value={this.state.inputValue} onChange={this.inputChange.bind(this)} />
    <button onClick={this.addList.bind(this)}> 增加项目 </button>
</div>
```

这时候你浏览效果虽然可以正常，但`console`里还是有红色警告提示的。大概意思是不能使用`for`.它容易和javascript里的for循环混淆，会提示你使用`htmlfor`。

```
<div>
    <label htmlFor="Sunshine">加入项目：</label>
    <input id="Sunshine" className="input" value={this.state.inputValue} onChange={this.inputChange.bind(this)} />
    <button onClick={this.addList.bind(this)}> 增加项目 </button>
</div>
```

这时候代码就正确了，可以实现点击后,激活标签了。

这节算是我总结的一些`JSX`中的坑吧，总结出来，希望小伙伴们少踩这些坑，能快速上手`React`。