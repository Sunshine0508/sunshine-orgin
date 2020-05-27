---
title: React实例
date: 2020-05-27 16:19:46
tags:
categories: react
---

### 让列表数据化

现在的列表还是写死的两个``标签，那要变成动态显示的，就需要把这个列表先进行数据化，然后再用`javascript`代码，循环在页面上。

我们先给list数组增加两个数组元素，代码如下：

```
constructor(props){
    super(props) //调用父类的构造函数，固定写法
    this.state={
        inputValue:'Sunshine' , // input中的值
        //----------主要 代码--------start
        list:['项目一','项目二']   
        //----------主要 代码--------end
    }
}
```

有了数据后，可以在`JSX`部分进行循环输出，代码如下：

```
render(){
    return  (
        <Fragment>
            <div>
                <input value={this.state.inputValue} onChange={this.inputChange.bind(this)} />
                <button> 增加项目 </button>
            </div>
            <ul>
                {
                    this.state.list.map((item,index)=>{
                        return <li>{item}</li>
                    })
                }
            </ul>  
        </Fragment>
    )
}
```

完成上面的步骤，数据就不再是固定的了，而是动态管理的，也为我们接下来的添加打下了基础，剩下的步骤也显得很简单了。

### 增加服务选项

要增加服务选项，我们需要再增加按钮上先绑定一个方法`this.addList`(这个方法目前还没有，需要我们接下来建立).

```
<button onClick={this.addList.bind(this)}> 增加项目 </button>
```

接下来就是把`this.addList`方法，代码如下：

```
//增加服务的按钮响应方法
addList(){
    this.setState({
        list:[...this.state.list,this.state.inputValue]
    })

}
```

这里需要说的是`...`这个是ES6的新语法，叫做扩展运算符。意思就是把list数组进行了分解，形成了新的数组，然后再进行组合。这种写法更简单和直观，所以推荐这种写法。

### 解决key值错误

高兴的同时其实是有一些隐患的，打开浏览器的控制台`F12`,可以清楚的看到报错了。这个错误的大概意思就是缺少`key值`。就是在用map循环时，需要设置一个不同的值，这个时React的要求。我们可以暂时用`index+item`的形式来实现。

```
<ul>
    {
        this.state.list.map((item,index)=>{
            return <li key={index+item}>{item}</li>
        })
    }
</ul> 
```

### 数组下标的传递

如果要删除一个东西，就要得到数组里的一个编号，这里指下标。传递下标就要有事件产生，先来绑定一个双击事件.代码如下:

```
<ul>
    {
        this.state.list.map((item,index)=>{
            return (
                <li 
                    key={index+item}
                    onClick={this.deleteItem.bind(this,index)}
                >
                    {item}
                </li>
            )
        })
    }
</ul>  
```

为了看着更清晰，我们在`return`部分加了`()`这要就可以换行编写`JSX`代码了.在`onClick`我们绑定了`deleteItem`方法.

### 编写deleteItem方法

绑定做好了,现在需要把`deleteItem`,在代码的最下方,加入下面的代码.方法接受一个参数`index`.

```
//删除单项服务
deleteItem(index){
    let list = this.state.list
    list.splice(index,1)
    this.setState({
        list:list
    })

}
```

其实这里边是有一个坑的,有的小伙伴肯定会认为下面的代码也是正确的.

```
//删除单项服务
deleteItem(index){
    this.state.list.splice(index,1)
    this.setState({
        list:this.state.list
    }) 
}
```

记住React是禁止直接操作state的,虽然上面的方法也管用,但是在后期的性能优化上会有很多麻烦,所以一定不要这样操作.这也算是我`React`初期踩的比较深的一个坑,希望小伙伴们可以跳坑.

