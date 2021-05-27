###1.浮动元素有什么特征？对父容器、其他浮动元素、普通元素、文字分别有什么影响？
####特征：
- 浮动元素的框可以向左或者向右移动，直到它的外边缘碰到父元素包含框或者另一个浮动元素的边框为止；浮动元素不在文档普通流之中，因此文档普通流中的块级元素感知不到浮动元素的存在。
-对父容器影响：
如果不对子元素设置左浮动，父元素的状态应该是被上下撑开的，在对子元素都设置浮动之后，父元素的高度变为0
![image.png](http://upload-images.jianshu.io/upload_images/8649258-ade338a99269846b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 对其他浮动元素的影响
![image.png](http://upload-images.jianshu.io/upload_images/8649258-372ba8afbfa58522.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 对普通元素的影响：
红框设置浮动之后，脱离普通流，普通元素例如绿框认为红框不存在，结果就是脱离文档流的元素覆盖了普通元素。
![image.png](http://upload-images.jianshu.io/upload_images/8649258-79219b7d5baf28b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 对文字的影响：
浮动元素脱离文档流之后，文字是可以感知其存在的，会为其留出位置
![image.png](http://upload-images.jianshu.io/upload_images/8649258-f64d248be6354f32.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/8649258-5614c8e54c472505.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


###2.清除浮动指什么？如何清除浮动？两种以上方法
- 清除浮动是指：清除浮动：清除浮动指的是运用clear属性去解决浮动父容器高度塌陷的问题，clear属性规定元素的哪一侧不允许其他浮动元素。
清除浮动方法：
- 方法1：根据要清除浮动的位置选择，clear：left，clear：right，clear：both
![image.png](http://upload-images.jianshu.io/upload_images/8649258-b630d26b24aaba64.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 方法2：添加无意义的标签
![image.png](http://upload-images.jianshu.io/upload_images/8649258-18a0ca85a6a481f6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 方法3 利用伪类元素
![image.png](http://upload-images.jianshu.io/upload_images/8649258-68cb1bfebb19237c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/8649258-e8e7f3d5f3c58355.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 方法4 bfc清除浮动
![image.png](http://upload-images.jianshu.io/upload_images/8649258-fd4d2b25e6ac8248.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


###3有几种定位方式，分别是如何实现定位的 ，参考点是什么，使用场景是什么
- relative 生成相对定位的元素，相对于元素本身正常位置进行定位，因此，left：20px会向元素的left位置添加20px
- absolute 生成绝对定位的元素，相对与static定位意外的第一个祖先元素进行定位，元素的位置通过left，top，right，bottom属性进行规定。正常情况下根节点是html
- fixed生成绝对定位的元素，相对于浏览器窗口进行定位。元素的位置通过left，top，right，bottom属性进行规定

###4.z-index有什么作用？如何使用？
- z-index属性设置元素的堆叠顺序。拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面。
- 通过设置z-index的值，值越大  优先级越高 元素的位置越在上面

###5.position：relative和负margin都可以使元素位置发生偏移？二者有什么区别？
- position：relative是相对于元素自己原有位置的偏移，margin是改变元素之间的相对位置
- 使用position:relative会使元素在原有基础上进行偏移但是文档流的位置还是在偏移前的位置，使用margin属性的时候文档流的位置已经做出改变
所以在没有设置浮动的情况下 使用 relative 会遮挡住普通元素，而使用margin不会遮挡普通元素

###6BFC是什么？如何生成BFC？BFC有什么作用？举例说明
- BFC全称是block format content
- 在为元素设置了以下属性中任何一个时就会形成块级格式化上下文：position：absolut，position：fixed，float，table-cell，inline-block，overflow：hidden，auto，scroll。
- BFC作用
 BFC可以用来清除浮动
- 举例：
在不使用bfc清除浮动前：由于为aside设置了浮动，aside脱离普通流，后面的content对aside进行了覆盖，文字对aside进行围绕。
![image.png](http://upload-images.jianshu.io/upload_images/8649258-a7b69b45e4623abe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
在为content加了overflow：hidden之后，浮动被清除
![image.png](http://upload-images.jianshu.io/upload_images/8649258-f6dd2cd886e222b4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###7在什么场景下回出现外边距合并？如何合并？如何不让相邻元素外边距合并？给个父子外边距合并的范例
- 边距合并：
![image.png](http://upload-images.jianshu.io/upload_images/8649258-5fb0f728e1fc69b2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 如何合并：
外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。
若两者都为正外边距以最大的外边距为准；
若存在负边距， 合并后的外边距为最大正外边距减去绝对值最大的负边距；
若无正外边距，则用0减去绝对值最大负边距。
-阻止合并：
![image.png](http://upload-images.jianshu.io/upload_images/8649258-59d9571bfbd302d0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 父子外边距合并：
在图中，只对h1设置了外边距，没有对ct设置外边距，但是发生了父子外边距合并，导致ct与box2之间产生了外边距
![image.png](http://upload-images.jianshu.io/upload_images/8649258-8fd37456fa1bbf80.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




##代码：
1.实现如下alert效果
https://xhrbtk.github.io/demos/test/task-10/task10-1.html
2.实现如下表单效果
https://xhrbtk.github.io/demos/test/task-10/task10-2.html
3.实现如下模态框效果
https://xhrbtk.github.io/demos/test/task-10/task10-3.html
4.实现如下导航效果
https://xhrbtk.github.io/demos/test/task-10/task10-4.html
