## 1.下面的代码输出多少？修改代码让 fnArri 输出 i。使用 两种以上的方法

```
var fnArr=[]
		for(var i =0;i<10;i++){
			fnArr[i]=function(){
				return i
			}
		}
		console.log(fnArr[3]())

		//输出10

```

改写 方法一：

```
var fnArr=[]
		for(var i=0;i<10;i++){
			fnArr[i]=(function(j){
				return function(){
					return j
				}
			})(i)
		}
		console.log(fnArr[4]()) //4

```

方法二

```
var fnArr=[]
		for (var i=0;i<10;i++){
			!function(i){
				fnArr[i]=function(){
					return i
				}
			}(i)
		}
		console.log(fnArr[5]())//5

```

## 2\. 封装一个汽车对象，可以通过如下方式获取汽车状态

```
var Car = (function(){
			var speed = 0;
		   	function setSpeed(s){
		       speed = s
		       return speed
		   	}
		   	function getSpeed(){
		   		return speed
		   	}
		   	function decelerate(){
		   		speed-=10
		   		return speed
		   	}
		   	function accelerate(){
		   		speed+=10
		   		return speed
		   	}
		   	function getStatus(){
		   		if (speed>0){
		   			return 'running'
		   		}
		   		else{
		   			return 'stop'
		   		}
		   	}
		   return {
		      setSpeed:setSpeed,
		      getSpeed:getSpeed,
		      accelerate:accelerate,
		      decelerate:decelerate,
		      getStatus:getStatus,
		   }
		})()
		Car.setSpeed(30);
		Car.getSpeed(); //30
		Car.accelerate();
		Car.getSpeed(); //40;
		Car.decelerate();
		Car.decelerate();
		Car.getSpeed(); //20
		Car.getStatus(); // 'running';
		Car.decelerate(); 
		Car.decelerate();
		Car.getStatus();  //'stop';
		//Car.speed;  //error

```

## 3.下面这段代码输出结果是? 为什么?

```
var a = 1;
		setTimeout(function(){
		    a = 2;
		    console.log(a);//第三个
		}, 0);
		var a ;
		console.log(a);//第一个
		a = 3;
		console.log(a);//第二个

		// 1,3,2
		//即使setTimeout时间间隔为0.也会在整个代码执行完成之后再执行

```

## 4.下面这段代码输出结果是? 为什么?

```
var flag = true;
		setTimeout(function(){
		    flag = false;
		},0)
		while(flag){}
		console.log(flag);
		//没有任何输出
		//setTimeout会在整个代码执行完毕之后再执行，但是由于flag始终为true，while函数会一直执行下去，所以setTimeout不会执行

```

## 5.下面这段代码输出？如何输出delayer: 0, delayer:1…（使用闭包来实现）

```
for(var i=0;i<5;i++){
			!function(i){
				setTimeout(function(){
	         	console.log('delayer:' + i );
				}, 0);
				console.log(i);
			}(i)}

```

## 6\. 如何获取元素的真实宽高

```
var teat= document.querySelector(".test")
getComputedStyle(test,pse).width  //获取元素的宽度，第二鸽参数为伪类，没有则不设置
getComputedStyle(test,pse).height //获取元素的宽度，第二鸽参数为伪类，没有则不设置

//兼容低版本IE的方式
function tureStyle(element,pse){
    return element.currentStyle ?
    element.currentStyle:window.getComputedStyle(element,pse);
}
var trueWidth=tureStyle(element,pse).width
var trueHeight=tureStyle(element,pse).height

```

## 7.URL 如何编码解码？为什么要编码？

*   URL的编码/解码方法
    1.decodeURI()
    2.decodeURIComponent()
    3.encodeURI()
    4.encodeURIComponent()
*   区别
    *   encodeURI方法不会对下列字符编码
        1.  ASCII字母
        2.  数字
        3.  ~!@#$&*()=:/,;?+’
    *   encodeURIComponent方法不会对下列字符编码
        1.  ASCII字母
        2.  数字
        3.  ~!*()'
            所以encodeURIComponent比encodeURI编码的范围更大。
            实际例子来说，encodeURIComponent会把 http:// 编码成 http%3A%2F%2F 而encodeURI却不会。
            ![image](http://upload-images.jianshu.io/upload_images/8649258-b46b8d65d0387ed5.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

*   为什么要编码
    *   HTTP协议中参数组件的传输是“key=value”键值对的形式，如果要传输多个参数就需要用“&”符号对键值对进行分隔。例如?name1=value1&name2=$value2,这样在服务器收到这种字符串的时候，会用“&”分隔出每一个参数，然后再用“=”来分隔出参数值。如果我的参数值中就包含=或者&这样的特殊子字符的时候,比如说“name1=value1”,其中value1的值是“va&lu=e1”，那么在传输过程中就会变成“name1=va&lu=e1”。用户传输的本意是只有一个键值对，但是服务器端会解析成两个键值对，这样就自然的产生了歧义。这时就需要对上述产生歧义的字符进行编码。[参考1](http://www.cnblogs.com/jerrysion/p/5522673.html)

## 8.补全如下函数，判断用户的浏览器类型

```
		function isAndroid(){
			return /Android/i.test(navigator.userAgent);
		}

		function isIphone(){
			return /Iphone/i.test(navigator.userAgent);
		}

		function isIpad(){
			return /Ipad/i.test(navigator.userAgent);
		}

		function isIos(){
			return /(Iphone)|(Ipad)/i.test(navigator.userAgent);
		}
```
