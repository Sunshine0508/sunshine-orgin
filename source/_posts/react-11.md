---
title: React进阶——父子组件的传值
date: 2020-05-30 13:05:56
tags:
categories: react
---

### 父组件向子组件传值

这里只介绍最实用的，最快速的上手方法。就是使用组件属性的形式父组件给子组件传值。比如：我们在`<sunshineItem>组件中加入content`属性，然后给属性传递`{item}`，这样就完成了父组件向子组件传值。

```
<sunshineItem content={item}/>
```

现在值已经顺利的传递了过去，这时候可以通过`this.props.xxx`的形式进行接受，比如传递过来的值，可以用如下代码进行接收。

```
import React, { Component } from 'react'; //imrc
class sunshineItem  extends Component { //cc

    render() { 
        return ( 
            <div>{this.props.content}</div>
         );
    }
}

export default sunshineItem;
```

### 子组件向父组件传递数据

现在要作这样一个功能：点击组件中的菜单项后，删除改菜单项。在前边的课程中已经学习了这个知识，知识现在组件拆分了，就涉及了一个字组件向父组件传递数据的知识需要掌握。

先来绑定点击事件，这时候当然是要在<sunshineItem>组件中绑定了，代码如下：

```
import React, { Component } from 'react'; //imrc
class sunshineItem  extends Component { //cc

    render() { 
        return ( 
            <div onClick={this.handleClick}>{this.props.content}</div>
         );
    }

    handleClick(){
        console.log('点击....')
    }

}

export default sunshineItem;
```

React有明确规定，子组件时不能操作父组件里的数据的，所以需要借助一个父组件的方法，来修改父组件的内容。

```
<ul>
    {
        this.state.list.map((item,index)=>{
            return (
                <sunshineItem 
                key={index+item}  
                content={item}
                index={index}
                //关键代码-------------------start
                deleteItem={this.deleteItem.bind(this)}
                //关键代码-------------------end
                />
            )
        })
    }
</ul> 
```

子组件

```
import React, { Component } from 'react'; //imrc
class sunshineItem  extends Component { //cc
		//--------------主要代码--------start
   constructor(props){
       super(props)
       this.handleClick=this.handleClick.bind(this)
   }
   //--------------主要代码--------end
    render() { 
        return ( 
            <div onClick={this.handleClick}>{this.props.content}</div>
         );
    }

    handleClick(){
        console.log('点击....',this.props.index)
        this.props.deleteItem(this.props.index)
    }

}

export default sunshineItem;
```

