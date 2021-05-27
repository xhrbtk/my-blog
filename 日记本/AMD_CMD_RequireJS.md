es6和commonjs
```
1. CommonJS 模块输出的是一个值的拷贝，ES6 模块输出的是值的引用。

CommonJS 模块输出的是值的拷贝，也就是说，一旦输出一个值，模块内部的变化就影响不到这个值。
ES6 模块的运行机制与 CommonJS 不一样。JS 引擎对脚本静态分析的时候，遇到模块加载命令import，就会生成一个只读引用。等到脚本真正执行时，再根据这个只读引用，到被加载的那个模块里面去取值。换句话说，ES6 的import有点像 Unix 系统的“符号连接”，原始值变了，import加载的值也会跟着变。因此，ES6 模块是动态引用，并且不会缓存值，模块里面的变量绑定其所在的模块。

作者：subwaydown
链接：https://juejin.im/post/5aaa37c8f265da23945f365c
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

es6
```
ES6 在语言标准的层面上，实现了模块功能，而且实现得相当简单，旨在成为浏览器和服务器通用的模块解决方案。其模块功能主要由两个命令构成：export和import。export命令用于规定模块的对外接口，import命令用于输入其他模块提供的功能。
```

- 为什么要使用模块化
1 解决命名冲突
2 便于依赖管理
3 提高代码的可读性
4 代码解耦，提高代码复用性
- CMD，AMD，CommonJS规范分别指什么？有哪些应用
1 AMD规范（异步模块定义）指定一种机制，在该机制下模块和依赖可以异步架子啊。这对浏览器端的异步加载尤其适用
```
AMD规范采用异步方式加载模块，模块的加载不影响它后面语句的运行。所有依赖这个模块的语句，都定义在一个回调函数中，等到加载完成之后，这个回调函数才会运行。这里介绍用require.js实现AMD规范的模块化：用require.config()指定引用路径等，用define()定义模块，用require()加载模块。

作者：subwaydown
链接：https://juejin.im/post/5aaa37c8f265da23945f365c
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```
```
// 定义模块 myModule.js
define(['dependency'], function(){
  var name = 'Byron';
  function printName(){
    console.log(name);
}
    return {
    printName: printName
  };
});

// 加载模块
require(['myModule'], function (my){
　 my.printName(); 
});


```
2 CommonJs是服务器端模块的规范，Node.js采用了这个规范。Node.js首先采用了js模块化的概念
```
commonJS用同步的方式加载模块。在服务端，模块文件都存在本地磁盘，读取非常快，所以这样做不会有问题。但是在浏览器端，限于网络原因，更合理的方案是使用异步加载。
```
（1）在一个模块中，存在一个自由的变量“require”,它是一个函数
       这个“require”函数接收一个模块标识符
       require返回外部模块所输出的API
（2）在一个模块中，会存在一个名为“exports”的自由变量，它是一个对象，模块可以在执行的时候把自身的API加入到其中
（3）模块必须使用exports对象来作为输出的唯一表示
```
//模块定义 myModel.js

var name = 'Byron';

function printName(){
console.log(name);
}

function printFullName(firstName){
console.log(firstName + name);
}

module.exports = {
printName: printName,
printFullName: printFullName
}

//加载模块

var nameModule = require('./myModel.js');

nameModule.printName();


```
3 CMD是SeaJs推广过程中产生的

```
// 定义模块 myModule.js
define(function(require, exports, module) {
var $ = require('jquery.js')
$('div').addClass('active');
});

// 加载模块
seajs.use(['myModule.js'], function(my){

});


```

- 使用requireJS完善入门任务15，包括如下功能
```
1首屏大图为全屏轮播
2有回到顶部功能
3图片区使用瀑布流布局（图片高度不一），下部有加载更多按钮，点击加载更多会加载更多数据（数据在后端 mock）
4（可选），使用r.js打包应用
```
[预览连接](http://js.jirengu.com/jemoj)(实现返回顶部，木桶布局加载)
[预览连接](http://js.jirengu.com/rosok/1/edit)(实现轮播，返回顶部，木桶布局加载)
















