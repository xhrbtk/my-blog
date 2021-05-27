- 问题1： apply、call 、bind有什么作用，什么区别
作用：改变函数内部this的指向；区别：bind返回一个新函数；call和apply，调用一个函数，传入函数执行上下文及参数，而call和apply之间的区别是call接收参数列表，而apply接收参数数组。相同之处：三种方法的第一个参数都是希望设置的this对象
- 问题2： 以下代码输出什么?
```
var john = { 
  firstName: "John" 
}
function func() { 
  alert(this.firstName + ": hi!")
}
john.sayHi = func
john.sayHi()   //弹出John:hi
```
- 问题3： 下面代码输出什么，为什么
```
func() 
function func() { 
  alert(this)
}
//输出为：[object Window]，在函数被直接调用是this绑定到全局对象。在浏览器中，window就是该全局对象
```
- 问题4：下面代码输出什么
```
document.addEventListener('click', function(e){
    console.log(this);
    setTimeout(function(){
        console.log(this);
    }, 200);
}, false);
//第一个this是document，第二个this是全局对象window
//在事件处理程序中，this代表事件源DOM对象（低版本IE有bug，指向了window）
```
- 问题5：下面代码输出什么，why
```
var john = { 
  firstName: "John" 
}

function func() { 
  alert( this.firstName )
}
func.call(john)
//输出John，因为call改变了this的指向，在这里call调用了func这个函数，并想函数传入参数john，之后函数执行弹出John
```
- 问题6： 以下代码有什么问题，如何修改
```
var module= {
  bind: function(){
    $btn.on('click', function(){
      console.log(this) //this指什么
      this.showMsg();
    })
  },
  
  showMsg: function(){
    console.log('饥人谷');
  }
}
//第一个this指向的是$btn对象，$btn对象并没有showMsg这个方法，所以下面this.showMsg
会出错
改正方法是让this指向对象本身，可以保存原来的this
var module= {
  bind: function(){
    var _this = this
    $btn.on('click', function(){
      console.log(self)
      self.showMsg();
    })
  },
  
  showMsg: function(){
    console.log('饥人谷');
  }
}


```
- 原型链相关问题
- 问题7：有如下代码，解释Person、 prototype、__proto__、p、constructor之间的关联。
```
function Person(name){
    this.name = name;
}
Person.prototype.sayName = function(){
    console.log('My name is :' + this.name);
}
var p = new Person("若愚")
p.sayName();

//p.__proto__.constructor==Person
//Person.prototype.constructor==Person
//p.constructor==Person
//Person 是构造函数， prototype 是构造函数的共有属性。 p是Person的实例，该实例有__proto__对象指向Person.prototype。constructor表示该实例的构造器，指向Person。
```
![image.png](http://upload-images.jianshu.io/upload_images/8649258-86830943c096124f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


- 问题8： 上例中，对对象 p可以这样调用 p.toString()。toString是哪里来的? 画出原型图?并解释什么是原型链。

-toString 是Object的prototype上的方法，所以p可以调用p.toString()

![image.png](http://upload-images.jianshu.io/upload_images/8649258-298590661a1bfdac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

原型链就是js在创建对象的时候，都会有一个叫做**proto**的内置属性，它指向创建他的函数对象的原型对象，所以在元素调用方法的时候，先从自己身上找，没有的话从创建它的函数的函数原型上找，再找不到的话从object的原型上找，如果还没有的话，就是没有了。这种逐级往上找的链式关系叫做原型链。





- 问题9：对String做扩展，实现如下方式获取字符串中频率最高的字符
```
var str = 'ahbbccdeddddfg';
 String.prototype.getMostOften=function(){
 	var dict={}
 	for(var i=0;i<this.length;i++){
 		if(dict[this[i]]){
 			++dict[this[i]]
 		}else{
 			dict[this[i]]=1
 		}
 	}
 	var count=0
 	var maxvalue
 	for(var key in dict){
 		if(dict[key]>count){
 			maxvalue=key
 			count=dict[key]
 		}
 	}
 	return maxvalue
 }
 var ch = str.getMostOften();

 console.log(ch); //d , 因为d 出现了5次
```
- 问题10： instanceOf有什么作用？内部逻辑是如何实现的？
 instanceOf用来判断一个对象是是否是一个构造函数的实例。假设当前对象是p1，内部是通过判断p1.__proto__ === Object.prototype是否相同来实现的，假如当前不相等，当前对象就会根据原型链往上找，p1.__proto__.__proto__ === Object.prototype，直到null，找到就返回true，否则为false。

- 继承相关问题
- 问题11：继承有什么作用?
继承可以使一个对象直接使用另一对象的属性和方法,增加代码复用，减少代码的复杂度，良好扩展对象
- 问题12： 下面两种写法有什么区别?
```
//方法1
function People(name, sex){
    this.name = name;
    this.sex = sex;
    this.printName = function(){
        console.log(this.name);
    }
}
var p1 = new People('饥人谷', 2)

//方法2
function Person(name, sex){
    this.name = name;
    this.sex = sex;
}

Person.prototype.printName = function(){
    console.log(this.name);
}
var p1 = new Person('若愚', 27);
```
方法一：将printName作为对象的自有方法定义，对象实例化后自身拥有这个方法，每次new出来实例，都会产生新的属性和方法，占用过多不必要的内存
方法二：将printName放在构造方法的prottotype属性中，实例化对象可以通过原型链查找调用这个方法使用原型的好处可以让所有对象实例共享它所包含的属性和方法。每次new出来实例，会产生新的属性，但方法都在共有的属性原型链是哪个，节省内存
- 问题13： Object.create 有什么作用？兼容性如何？
 Object.create ()方法会使用指定的原型对象及其属性去创建一个新的对象，实现继承

- 问题14： hasOwnProperty有什么作用？ 如何使用？
hasOwnProperty是Object.prototype的一个方法，可以判断一个对象是否包含自定义属性而不是原型链上的属性，hasOwnProperty是JavaScript中唯一一个处理属性但是不查找原型链的函数
```
m.hasOwnProperty('name'); // true   判断name是否是m的自定义属性

```
- 问题15：如下代码中call的作用是什么?
```
function Person(name, sex){
    this.name = name;
    this.sex = sex;
}
function Male(name, sex, age){
    Person.call(this, name, sex);    //把环境改到自己的作用域内，这样就可以使用Person里定义的属性了。
    this.age = age;
}

```
- 问题16： 补全代码，实现继承 
```
function Person(name, sex) {
            this.name = name
            this.sex = sex
        }

        Person.prototype.printName = function() {
            console.log('My name is '+ this.name)
        }

        function Male(name, sex, age) {
            Person.call(this, name, sex)
            this.age = age
        }

        Male.prototype = Object.create(Person.prototype)
        Male.prototype.constructor = Male

        Male.prototype.getAge = function(){
            return this.age
        }

        var ruoyu = new Male('若愚', '男', 27);
        ruoyu.printName();
```
