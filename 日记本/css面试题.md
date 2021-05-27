## 如何实现一个三角形
- 写一个div，宽高设置为0px，然后将border中的一边设为有颜色的，其他均设置为透明。
```
div{
		width: 0px;
		height: 0px;
		border-left: 100px solid green;
		border-right: 100px solid transparent;
		border-bottom: 100px solid transparent;
		border-top: 100px solid transparent;

	}
```
### 如何实现一个圆环:写一个div，设置div的宽高为100px，设置border-radius：50%，之后设置border：10px solid red；这样就得到 了一个红色的圆环。
```
div{
		width: 100px;
		height: 100px;
		border-radius: 50%;
		border: 10px solid red;
	}

```
### div边距合并：当一个元素出现在另一个元素上面时，第一个元素的底外边距与第二个元素的顶外边距发生叠加。此时外边距的高度等于发生叠加的外边距的高度中的较大者。
顺丰面试：
```
1.如何实现一个三角形
2.如何实现一个圆环
3,。js基本数据类型
4.es6你了解哪些
5.跨域
6.数组都有哪些方法
7.深拷贝
8，深拷贝和浅拷贝有什么区别
9，http和https有什么区别
10.vue双向绑定原理
11，vue指令
12，http状态码
13，前端性能优化
14，原型原型链
15.给你一个数组，如何统计数组里面字母出现的次数，以及都有哪些字母
16.v-if和v-show有神马区别
17.dom都有哪些绑定函数
18.打包工具有哪些
19，你常用的git明亮有哪些，作用是什么

```
