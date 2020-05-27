---
title: React响应式设计原理和数据绑定
date: 2020-05-27 16:10:16
tags:
categories: react
---

### 响应式设计和数据绑定

`React`不建议你直接操作`DOM`元素,而是要通过数据进行驱动，改变界面中的效果。React会根据数据的变化，自动的帮助你完成界面的改变。所以在写React代码时，你无需关注DOM相关的操作，只需要关注数据的操作就可以了（这也是React如此受欢迎的主要原因，大大加快了我们的开发速度）。

数据定义一般放在构造函数里`constructor`

```
//js的构造函数，由于其他任何函数执行
constructor(props){
    super(props) //调用父类的构造函数，固定写法
    this.state={
        inputValue:'' , // input中的值
        list:[]    //服务列表
    }
}
```

在`React`中的数据绑定和`Vue`中几乎一样，也是采用`字面量`(我自己起的名字)的形式，就是使用`{}`来标注，其实这也算是js代码的一种声明。比如现在我们要把`inputValue`值绑定到`input`框中，只要写入下面的代码就可以了。其实说白了就是在JSX中使用js代码。

```
<input value={this.state.inputValue} /> 
```

现在需要看一下是不是可以实现绑定效果，所以把`inputValue`赋予一个'Sunshine'，然后预览看一下效果。在这里我们并没有进行任何的`DOM`操作，但是界面已经发生了变化，这些都时`React`帮我们作的，它还会自动感知数据的变化。

### 绑定事件

这时候你到界面的文本框中去输入值，是没有任何变化的，这是因为我们强制绑定了`inputValue`的值。如果要想改变，需要绑定**响应事件**，改变`inputValue`的值。比如绑定一个改变事件，这个事件执行`inputChange()`(当然这个方法还没有)方法。

```
<input value={this.state.inputValue} onChange={this.inputChange} />
```

现在还没有`inputChange()`这个方法，在`render()`方法的下面建立一个`inputChange()`方法，代码如下：

```
inputChange(e){
    console.log(e.target.value);
}
```

这时候控制台是可以打印出输入的值的。看到获得了输入的值，想当然的认为直接改变`inputValue`的值就可以了(错的).

```
inputChange(e){
    console.log(e.target.value);
    this.state.inputValue=e.target.value;
}
```

写完后再进行预览，会发现程序直接报错了（加项服务还真的有点难度...........）。

其实我们范了两个错误：

1. 一个是`this`指向不对，你需要重新用`bind`设置一下指向(ES6的语法)。
2. 另一个是`React`中改变值需要使用`this.setState`方法。

第一个错误很好解决，直接再`JSX`部分，利用`bind`进行绑定就好。

```
 <input value={this.state.inputValue} onChange={this.inputChange.bind(this)} />
```

这步做完，我们还需要加入`setState`方法，改变值。代码如下:

```
inputChange(e){
    // console.log(e.target.value);
    // this.state.inputValue=e.target.value;
    this.setState({
        inputValue:e.target.value
    })
}
```

现在测试一下，输入框可以改变值了，里边设计了`React`的重要思想。