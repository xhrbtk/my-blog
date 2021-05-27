- UI事件，当用户与页面上的元素交互时触发
- 焦点事件，当元素获得或者失去焦点时触发
- 鼠标事件，当用户通过鼠标在页面上执行操作时触发
- 滚轮事件，当使用鼠标滚轮使触发
- 文本事件，当在文档中输入文本时触发
- 键盘事件，当用户通过键盘在页面上执行操作时触发





题目1： DOM0 事件和DOM2级在事件监听使用方式上有什么区别？
- 通过javascript制定事件处理程序的传统方式。就是将一个函数赋值给一个事件处理属性。第四代web浏览器出现，至今为所有浏览器所支持。优点，简单且具有跨浏览器的优势。
```
    例：var btn = document.getElementById("btn");
            btn.onclick = function(){
                alert(this.id);//this指定当前元素btn

            }
```
- 删除DOM0事件处理程序，只要将对应事件属性置为null即可。
btn.onclick = null;
缺点：一个事件处理程序只能对应一个处理函数。
- DOM2级事件规定事件流包括三个阶段，事件捕获阶段，处于目标阶段，事件冒泡阶段，首先发生的是事件捕获，为截取事件提供机会，然后是实际目标接收事件，最后是冒泡阶段
- DOM2级事件处理方式指定了，添加事件处理程序和删除事件处理程序的方法。分别是：
    addEventListener(eventName,func,isPuhuo);
    removeEventListener(eventName,func,isPuhuo);
```
接受3个参数：要处理的事件名，
作为事件处理程序的函数，和一个布尔值。
最后这个布尔值参数如果是true，
表示在捕获阶段调用事件处理程序，
如果是false，表示在冒泡阶段调用事件处理程序。
一般都设置为false
btn.addEventListener("click",handler,false)
var btn=document.getElementById("mybtn")
btn.addEventListener("click",function(){})
//////////////////////////////////////////////////////////////
var handler=function(){alert(this.id)}
btn.addEventListener("click",handler,false)
btn.removeEventListener("click",handler,false)
```
- IE中的DOM2级事件处理
      d)IE中的DOM2级事件处理使用了attachEvent和detachEvent来实现

题目2： attachEvent与addEventListener的区别？
- attachEvent是IE有的方法，它不遵循W3C标准，而其他的主流浏览器如FF等遵循W3C标准的浏览器都使用addEventListener，所以实际开发中需分开处理。

- 多次绑定后执行的顺序是不一样的，attachEvent是后绑定先执行，addEventListener是先绑定先执行。
- 绑定时，attachEvent必须带on，如onclick，onmouseover等，而addEventListener不能带on，如click，mouseover。
- attachEvent仅需要传递两个参数，而addEventListener需要传递三个参数，这里牵扯到“事件流”的概念。侦听器在侦听时有三个阶段：捕获阶段、目标阶段和冒泡阶段。顺序为：捕获阶段（根节点到子节点检查是否调用了监听函数）→目 标阶段（目标本身）→冒泡阶段（目标本身到根节点）。此处的参数确定侦听器是运行于捕获阶段、目标阶段还是冒泡阶段。 如果将 useCapture 设置为 true，则侦听器只在捕获阶段处理事件，而不在目标或冒泡阶段处理事件。 如果useCapture 为 false，则侦听器只在目标或冒泡阶段处理事件。 要在所有三个阶段都侦听事件，请调用两次 addEventListener，一次将 useCapture 设置为 true，第二次再将useCapture 设置为 false。 

题目3： 解释IE事件冒泡和DOM2事件传播机制？
- DOM2事件：事件流包括三个阶段：事件捕获阶段，处于目标阶段，事件冒泡阶段
- IE的事件冒泡：事件开始时由最具体的元素接收，然后逐级向上传播到较为不具体的元素

题目4：如何阻止事件冒泡？ 如何阻止默认事件？
- stopPaopagation()方法可以停止事件在DOM层次的传播，即取消进一的事件捕获或冒泡。我们可以在button的事件处理程序中调用stopPropagation()从而避免注册在body上的事件发生
```
document.getElementsByTagName('a').onclick = function (e) {
e.preventDefault();
}
```
- 要阻止事件的默认行为，可以使用preventDefault()
方法，前提是cancelable值为true，比如我们可以阻止链接导航这一默认行为
```
document.getElementsByTagName('a').onclick = function (e) {
e.preventDefault();
}
```


```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>json</title>
</head>
<body>
<ul class="ct">
    <li>这里是</li>
    <li>饥人谷</li>
    <li>前端6班</li>
</ul>
<script>
//普通方式
var li=document.querySelectorAll('.ct li')
for(var i=0;i<li.length;i++){
	li[i].id=i;
	li[i].onclick=function(){
		index=this.id;
		console.log(li[index].innerHTML)
	}
}
//事件代理方式
var ct=document.querySelector('.ct')
ct.addEventListener('click',function(e){
if(e.target.tagName.toLowerCase() === 'li'){
  console.log(e.target.innerHTML)
}	
})
</script>
</body>
</html>
```

题目6： 补全代码，要求：

当点击按钮开头添加时在<li>这里是</li>元素前添加一个新元素，内容为用户输入的非空字符串；当点击结尾添加时在最后一个 li 元素后添加用户输入的非空字符串.
当点击每一个元素li时控制台展示该元素的文本内容。
```

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>json</title>
</head>
<body>
<ul class="ct">
    <li>这里是</li>
    <li>饥人谷</li>
    <li>任务班</li>
</ul>
<input class="ipt-add-content" placeholder="添加内容"/>
<button id="btn-add-start">开头添加</button>
<button id="btn-add-end">结尾添加</button>
<script>
var btnstart=document.querySelector("#btn-add-start")
var btnend=document.querySelector('#btn-add-end')
var input=document.querySelector('.ipt-add-content')
var ul=document.querySelector('.ct')

//点击开头添加
btnstart.onclick=function(){
	var li=document.querySelectorAll('.ct li')
	var testli=document.createElement("li")
	if(input.value!=""){
		testli.innerHTML=input.value;
		ul.insertBefore(testli,li[0])	
	}
	else{
		alert("没有输入内容")
	}
}

//点击结尾添加
btnend.onclick=function(){
	var parse=document.createElement("li")
	if(input.value!=""){
		parse.innerHTML=input.value;
		ul.appendChild(parse)	
	}
	else{
		alert("没有输入内容")
	}
}

//点击li控制台输出
 ul.onclick= function(e){
      if(e.target.tagName.toLowerCase() === 'li'){
       console.log(e.target.innerText);
      }
  }
</script>
</body>
</html>
```
题目7： 补全代码，要求：当鼠标放置在li元素上，会在img-preview里展示当前li元素的data-img对应的图片。
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>json</title>
</head>
<style>
	.img-preview{
		width: 300px;
		height:300px;
		border: 1px solid red;
		overflow: hidden;
	}
</style>
<body>

<ul class="ct">
    <li data-img="https://ss1.baidu.com/9vo3dSag_xI4khGko9WTAnF6hhy/image/h%3D300/sign=0c04666a8acb39dbdec06156e01709a7/2f738bd4b31c8701704bb0662c7f9e2f0608ffb5.jpg">鼠标放置查看图片1</li>
    <li data-img="https://ss0.baidu.com/7Po3dSag_xI4khGko9WTAnF6hhy/image/h%3D300/sign=c7cfddeca64bd1131bcdb1326aaea488/7af40ad162d9f2d358761d70a2ec8a136227cccd.jpg">鼠标放置查看图片2</li>
    <li data-img="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1512563705294&di=9d7e415079b926972ea4429aa345c8a8&imgtype=0&src=http%3A%2F%2Fd.hiphotos.baidu.com%2Fimage%2Fpic%2Fitem%2Fd53f8794a4c27d1e79d2125a10d5ad6edcc438b3.jpg">鼠标放置查看图片3</li>
</ul>
<div class="img-preview"></div>
<script>
var ct=document.querySelector(".ct")
var preview=document.querySelector(".img-preview")
var li=document.querySelectorAll(".ct li")
var img=document.createElement("img")
preview.appendChild(img)
//利用普通方式解决
for(var i=0;i<li.length;i++){
	li[i].id=i
	li[i].onmouseover=function(){
		var index=this.id
		var dataimg=li[index].getAttribute("data-img")
		img.setAttribute("src",dataimg)
	}
}
//利用事件代理的方式解决
ct.addEventListener('mouseover',function(e){
if(e.target.tagName.toLowerCase() === 'li'){   
        var target=e.target
	var dataimg=target.getAttribute("data-img")
	img.setAttribute("src",dataimg)
}	
})
</script>
</body>
</html>
```
- 事件代理应用场景，页面上有一些新增元素也需要绑定事件时

