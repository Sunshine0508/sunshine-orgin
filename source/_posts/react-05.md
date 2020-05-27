---
title: HelloWord 和组件的讲解
date: 2020-05-27 14:54:59
tags:
categories: react
---

写下下面四行代码：

```
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'
ReactDOM.render(<App />,document.getElementById('root'))
```

上面的代码，我们先引入了React两个必要的文件，然后引入了一个APP组件，目前这个组件还是没有的，需要一会建立。然后用React的语法把APP模块渲染到了`root` ID上面.这个rootID是在`public\index.html`文件中的。

这样入口文件就写好了，这时候就需要写APP组件了。

### app组件的编写

现在写一下App组件，这里我们采用最简单的写法，就输出一个`Hello Sunshine`,就可以了。

```
import React, {Component} from 'react'

class App extends Component{
    render(){
        return (
            <div>
                Hello Sunshine
            </div>
        )
    }
}
export default App;
```

这里会出现一个不能理解的地方，就是：

```
import React, {Component} from 'react'
```

这其实是ES6的语法-解构赋值，如果你分开写就比较清楚了，你可以把上面一行代码写成下面两行.

```
import React from 'react'
const Component = React.Component
```

当我们这两个文件都编写完成后，可以在终端使用`npm start`命令，来看一下我们编写的结果了。

**总结：**React的主要优势之一就是组件化编写，这也是现代前端开发的一种基本形式。所以我们在学习React的时候就要多用这种思想，只有不断练习，我们才能在工作中得心应手，轻松自如。小伙伴们也动手作一下吧。