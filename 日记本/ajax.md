ajax是什么？有什么作用？

- ajax是一种技术方案，但并不是一种新技术，它以来的是现有的CSS/HTML/JavaScript。而其中最核心的以来是浏览器提供的XMLHttpRequest对象，是这个对象使得浏览器可以发送HTTP请求与接收HTTP响应

-  前后端开发连雕需要注意哪些事情？后端接口完成前如何mock数据？
- 约定好页面需要的数据和数据类型
- 约定接口名称
- 约定请求参数
- 约定响应格式，例如成功返回什么消息，失败返回什么消息
- 使用server-mock等工具搭建环境,例如easy-mock和githubpages mock数据

- 点击按钮，使用ajax获取数据，如何在数据到来之前放置重复点击？
```
var isLoading=false  //状态锁，用于判断是否在加载数据
btn.addEventListener('click',function(){
if(isLoading){
return   //如果正在请求数据，那这次点击什么都不做
}
//执行到这里说明  没有正在发出的请求，那后面就可以发请求
isLoading=true  //发请求之前做个标记加锁
ajax(xxx)   //请求数据
isLoading=false  //数据到来之后 解锁
})
```
- ajax是怎么实现的，有什么特点
> ajax是很多种结束的集合体。其中包括浏览器的xhr对象，他是负责为你开通另一条连接通道，可以传递信息。js是负责调用xhr对象与后天进行交互媒介。xml是一种数据格式，用于服务器应答传递信息的格式，处理xml外，还可以使用任何的文本格式，包括text，html，json等。
参考：(https://zhidao.baidu.com/question/394980725.html)

- Ajax readyState的五种状态
> 0 (未初始化)还没有调用send方法
1（载入）已调用send方法，正在发送请求
2（载入完成）send方法执行完成，已经接受到全部响应内容
3（交互）正在解析响应内容
4（完成）响应内容解析完成， 可以在客户端调用了
参考(http://blog.163.com/freestyle_le/blog/static/183279448201269112527311/)
- 加载更多
[加载更多](https://github.com/xhrbtk/demos/tree/master/fuwuqi/jiazaigengduo)
