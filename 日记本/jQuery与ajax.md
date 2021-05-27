题目1：jQuery 中， $(document).ready()是什么意思？
- $(document).ready()方法是为了防止文档在完全加载之前运行jQuery代码。若在文档未完全加载前就运行函数。操作可能失败，必须在文档加载完后执行操作，可使用ready时间，作用相当于把JS写到body末尾
- 以下两种语法全部是等价的：
```
$(document).ready(handler)
$(handler)
经常使用如下形式：
$(function(){
console.log("123")
})
```
题目2：$node.html()和$node.text()的区别?
- $node.html()返回所有选择元素内的html内容，包含html标签和文本内容
- $node.text(),返回所选择元素内的文本内容，不包含html标签，只包含文本内容
-$node.html()可以设置元素的html内容
-$node.text()可以设置元素的文本但是不能设置html内容
题目3：$.extend 的作用和用法?
- 当我们提供两个或多个对象给$.extend()，对象的所有属性都添加到目标对象中
- 如果只有一个参数提供给$.extend(),这意味着目标参数被省略。在这种情况下，jQuery对象本身被默认为目标对象。这样，我们可以在jQuery的命名空间下添加新的功能。这对于插件开发者希望向jQuery中添加新函数时是很有用的
- 目标对象（第一个参数）将被修改，并且通过$.extend()返回。然而，如果我们想保留原对象，我们可以通过传递一个空对象作为目标对象
- 在默认情况下，通过$.extend()合并操作不是递归的
- 如果第一个对象的属性本身是一个对象或数组，那么它将完全用第二个对象相同的key重写一个属性。这些值不会被合并。如果将true作为该函数的第一个参数，那么会在对象上进行递归的合并。
```
var obj1={a:1,b:2}
var obj2 = {b:2, c:3}
var obj3 = {b:3, d:5}
var object=$.extend({},obj1,obj2)  //{a: 1, b: 2, c: 3}
var o=$.extend(obj1,obj2,obj3)  //{a: 1, b: 3, c: 3, d: 5}
```
题目4：jQuery 的链式调用是什么？
- 链式调用的原理：jQuery节点在调用api后都会返回节点自身，类似于：
```
var obj={
a:1,
func:function(){
   this.a+=1
return this
}
}
obj.func().func()
console.log(obj.a)
```
- 在对象上一次性调动多个方法
```
$(".box").find("p").hide()
```
- 实现add(1)(2)(3)
```
function add (num) {
    var count = num;
    var _b = function(l){
        count += l;
        return _b
    }
    _b.valueOf = function(){
        return count
    }
    return _b
}
var c = add(1)(2)(3);
console.log(c)    //6
```

题目5：jQuery 中 data 函数的作用
- data()方法向被选元素附加数据，或者从被选元素获取数据。
```
从被选元素中返回附加的数据
$(selector).data(name)   //name,规定要取回的数据的名称
向元素附加数据
$(selector).data(name,value)   //name规定要设置的数据的名称，value规定要设置的数据的值
```
题目6：写出以下功能对应的 jQuery 方法：
     
- 给元素$node添加class  active，给元素删除class active
```
$node.addClass('active')
$node.removeClass('active')
```
-展示元素$node,隐藏元素$node
```
$node.show()
$node.hide()
```
- 获取$node元素的属性：id ,src,title
```
$node.attr("id")
$node.attr("src")
$node.attr("title")
//修改
$node.attr("id","btn")
$node.attr("src","http://www.baidu.com")
$node.attr("title","button")
```
- 给$node添加自定义属性data-src
```
$node.attr('data-src',' ')
```
- 在$ct内部最开头添加元素$node
```
$ct.prepend($node)
```
- 在$ct内部最末尾添加元素$node
```
$ct.append($node)
```
- 删除$node
```
$node.remove()
$node.detach()
```
- 把$ct里内容清空
```
$ct.empty()
```
- 在$ct里设置html<div class="btn"></div>
```
$ct.html("<div class=" btn  ">")
```
- 获取、设置$node 的宽度、高度(分别不包括内边距、包括内边距、包括边框、包括外边距)
```
$node .width()
$node.height()
$node.innerHeight()
$node.innerWidth()
$node.outerHeight()
$node.outerWidth()
$node.outerHeight(true)
$node.outerWidth(true)
```
- 获取窗口滚动条垂直滚动距离
```
$(window).scrollTop()
```
- 获取$node到根节点水平、垂直偏移距离
```
$node.offset()
```
- 修改$node的样式，字体颜色设置红色，字体大小设置14px
```
$node.css({'color':'red','font-size':'14px'})
```
- 遍历结点，把每个节点里面的文本内容重复一遍
```
$( "li" ).each(function( index ) {
  console.log( index + ":" + $(this).text() );
});
```
- 从$ct里查找class为.item的子元素
```
$ct.find(".item")
```
- 获取$ct里面的所有孩子
```
$ct.children()
```
- 对于$node,向上找到class为.ct的父亲，再从该父亲找到.panel的孩子
```
$node.parent('.ct').find('.panel')
```
- 获取选择元素的数量
```
$node.length
```
- 获取当前元素在兄弟中的排行
```
$(this).index()
```
题目7：用jQuery实现以下操作
-  当点击$btn 时，让 $btn 的背景色变为红色再变为蓝色
- 当窗口滚动时，获取垂直滚动距离
- 当鼠标放置到$div 上，把$div 背景色改为红色，移出鼠标背景色变为白色
- 当鼠标激活 input 输入框时让输入框边框变为蓝色，当输入框内容改变时把输入框里的文字小写变为大写，当输入框失去焦点时去掉边框蓝色，控制台展示输入框里的文字
-  当选择 select 后，获取用户选择的内容
[预览连接](http://js.jirengu.com/fayaj)
题目8用 jQuery ajax 实现如下效果。
[加载新闻](http://js.jirengu.com/hohij)
题目9(选做)：

实现一个天气预报页面，UI 如下图所示(仅供参考，可自由发挥)。数据接口:

1.  获取天气
    *   接口：http(s)://weixin.jirengu.com/weather
    *   服务端支持 CORS 跨域调用，前端可直接使用 ajax 获取数据，返回数据以及使用方式参考

        [http://api.jirengu.com

        114](http://api.jirengu.com/) 
2.  更多接口
    *   参考

        [http://api.jirengu.com

        114](http://api.jirengu.com/)
