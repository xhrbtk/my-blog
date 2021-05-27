题目1： dom对象的innerText和innerHTML有什么区别？
- innerText是一个可写属性，返回元素内包含的文本内容，在多层次的时候会按照元素又浅到深的顺序拼接其内容
- innerHTML属性作用和innerText类似，但是不是返回元素的文本内容，而是返回元素的HTML结构，在写入的时候也会自动构建DOM

题目2： elem.children和elem.childNodes的区别？
- childNodes：标准的，返回指定元素的子元素集合，包括HTML属性，所有属性，文本。可以通过nodeType来判断是哪种类型的节点，只有当nodeType==1时才是元素节点，2是属性节点，3是文本节点。
- children：非标准的，它返回指定元素的子元素集合。经测试，它只返回HTML节点，甚至不返回文本节点。且在所有浏览器下表现惊人的一致。和childNodes 一样，在Firefox下不支持()取集合元素。因此如果想获取指定元素的第一个HTML节点，可以使用children[0]来替代上面的 getFirst函数。需注意children在IE中包含注释节点。
- 有时候需要获取指定元素的第一个HTML子节点（非属性/文本节点），最容易想到的就是firstChild 属性。代码中第一个HTML节点前如果有换行，空格，那么firstChild返回的就不是你想要的了。可以使用nodeType来判断下。

题目3：查询元素有几种常见的方法？ES5的元素选择方法是什么?

- getElementById()
- getElementsByClassName()
- getElementsByTagName()  返回指定标签的元素
- getElementsByBName() 返回拥有name属性的html元素
- querySelector() 返回匹配指定的css选择器的元素结点。如果有多个节点满足匹配条件，则返回第一个匹配的节点。如果没有发现匹配的节点，则返回null
- querySelector()类数组对象

题目4：如何创建一个元素？如何给元素设置属性？如何删除属性
- 创建元素：createElement()用来生成HTML元素结点,createTextNode()方法用来生成文本结点，参数为所要生成的文本节点的内容。
- createDocumentFragment()方法生成一个DocumentFragment对象，var docFragment=document.createDocumentFragment();
DocumentFragment对象是一个存在于内存的Dom片段，但是不属于当前文档，常常用来生成较负责的dom结构，然后插入当前文档。这样做的好处在与，因为documentFragment不属于当前文档，对它的任何改动，都不会引发网页的重新渲染，比直接修改当前文档的dom有更好的性能体现。
- getAttribute()  获取元素的attribute值
- createAttribute()  生成一个新的属性对象结点，并返回
- setAttribute()  用于设置元素属性
- removeAttribute() 删除属性

题目5：如何给页面元素添加子元素？如何删除页面元素下的子元素?
- appendChild()  添加
- insertBefore()  插入
- replaceChild()  替换
- removerchild()  删除

题目6： element.classList有哪些方法？如何判断一个元素的 class 列表中是包含某个 class？如何添加一个class？如何删除一个class?
```
var title=document.querySelector('.title')
title.classList.add('active')  //添加一个class
title.classList.remove('active') //删除一个class
title.classList.contains('title')   //判断一个元素的class列表中是否包含title
```
题目7： 如何选中如下代码所有的li元素？ 如何选中btn元素？
```
<div class="mod-tabs">
   <ul>
       <li>list1</li>
       <li>list2</li>
       <li>list3</li>
   </ul>
   <button class="btn">点我</button>
</div>
//选中所有li元素 document.getElementsByTagName('li')
                          document.querySelectorAll("#mod-tabs  li")
//选中btn元素：document.getElementsByClassName('btn')
```
