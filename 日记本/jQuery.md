
题目1： jQuery 能做什么？
 - 选择网页元素
- 改变结果集
- 元素的操作：取值和赋值
- 元素的操作：移动
- 元素的操作：复制、删除和创建
- 工具方法
- 事件操作
- 特殊效果
- AJAX

题目2： jQuery 对象和 DOM 原生对象有什么区别？如何转化？
- jQuery 对象是通过jQuery包装DOM对象后产生的对象
```
//DOM对象转换成jQuery对象
 var $cr-$("#cr")
//jQuery对象转换成DOM对象
var cr=$cr[0]
```
题目3：jQuery中如何绑定事件？bind、unbind、delegate、live、on、off都有什么作用？推荐使用哪种？使用on绑定事件使用事件代理的写法？
- 在1.7之前的版本中jQuery处理事件有多个方法，作用各不相同，后来同一的使用on/off方法
- on(events[,selector][,data],handler(eventObject))
   - events:一个或多个空格分割的事件类型和可选的命名空间，或仅仅是命名空间，比如“click”，“keydown.myPlugin”,或者“.myPlugin”
   - selector:一个选择器字符串，用于过滤出被选中的元素中能出发事件的后代元素。如果选择器是null或者忽略了该选择器，那么被选中的元素总是能出发事件
  - data：当一个时间被出发时，要传递给事件处理函数的event.data
  - handleer(eventObject):事件被触发时，执行的函数。若该函数只是要执行return  false的话，那么该参数位置可以直接携程false
```
$('.box ul').on('click', 'li', function(){
  var str = $(this).text()
  $('#wrap').text(str)
})

```
题目4：jQuery 如何展示/隐藏元素？

- .show()
- .hide()
- .fadeIn()
- .fadeOut()
- .fadeToggle()
- .slideDown()
- .slideUp()
- .slideToggle()
- .animate

题目5： jQuery 动画如何使用？
.animate( properties [, duration ] [, easing ] [, complete ] )
- properties是一个css属性和值的对象，动画将根据这组对象移动
- duration (default: 400)：一个字符串或者数字决定动画将运行多久。默认值: "normal"， 三种预定速度的字符串("slow", "normal", 或 "fast"或表示动画时长的毫秒数值(如：1000) ）
- easing (default: swing)：一个字符串，表示过渡使用哪种缓动函数。jQuery自身提供"linear" 和 "swing"，其他效果可以使用jQuery Easing Plugin插件
- step：每个动画元素的每个动画属性将调用的函数。这个函数为修改Tween 对象提供了一个机会来改变设置中得属性值。
- complete：在动画完成时执行的函数


题目6：如何设置和获取元素内部 HTML 内容？如何设置和获取元素内部文本？
- 设置和获取元素内部HTML内容
 设置：$('div').html("<span>你喜欢什么</span>")
 获取：$('div').html()
- 设置和获取元素内部文本
  设置：$('div').text("123")
   获取：$('div').text()


题目7：如何设置和获取表单用户输入或者选择的内容？如何设置和获取元素属性？

- 设置和获取表单用户输入或者选择的内容：
获取：$("input").val()
设置：$("input").val("hello")
- 设置和获取元素属性
获取：$(".img").attr()
设置：$("img").attr("src","http"//www.baidu.com")
 

###题目8
[划过显示清单](http://js.jirengu.com/cined/1)
###题目9
[切换案例](http://js.jirengu.com/gekiz)
###题目10
[点击添加](http://js.jirengu.com/civaj)
##题目11
[左右切换](http://js.jirengu.com/zewil)













- 为什么要用jQuery

DOM API
   - 难用
  - 存在兼容性问题
   - 功能太少，不能与时俱进

JQrery
  - 兼容性好
  - API友好
  - 功能强大，与时俱进

什么时候适合用jQuery
  - DOM操作较多（事件监听）
- 简单的AJAX
- 需要兼容多款浏览器

什么时候不用jQuery
- 页面交互极为简单
- 页面对流量有苛求的要求
- 上级强制。团队已经有了jQuery的代替品


- 如果要兼容ie678，需要用jquery1.xxx

