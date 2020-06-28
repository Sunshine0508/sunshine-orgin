---
title: React高级——axios数据请求
date: 2020-06-28 15:22:46
tags:
categories: react
---

### 安装axios

`Axios`的安装可以使用npm来进行安装，你可以直接在项目根目录下，输入下面的代码。

***npm install -save axios***

安装好`axiso`之后，需要在使用ajax的地方先引入`axios` 

```
import axios from 'axios'
```

引入后，可以在`componentDidMount`生命周期函数里请求ajax，我也建议在`componentDidMount`函数里执行，因为在render里执行，会出现很多问题，比如一直循环渲染；在`componentWillMount`里执行，在使用RN时，又会有冲突。所以强烈建议在`componentDidMount`函数里作`ajax`请求。

```
componentDidMount(){
axios.post('https:...')
.then((res)=>{console.log('axios 获取数据成功:'+JSON.stringify(res)) })
.catch((error)=>{console.log('axios 获取数据失败'+error)})
}
```

