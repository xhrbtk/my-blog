##使用数组拼接出如下字符串 ，其中styles数组里的个数不定
```
	var prod = {
    name: '女装',
    styles: ['短款', '冬季', '春装']
};

function getTpl(data){
	var str1='';
	for(var key in data){
		// 如果是字符串
		if(typeof data[key]==='string'){
			str1+='<dt>'+data[key]+'</dt>'
		}
		// 如果是对象
		else{
			for(var i=0;i<data[key].length;i++){
				str1+='<dd>'+data[key][i]+'</dd>'
			}
		}
	}
	return '<dl class="product">'+str1+'</dl>'
};
var result = getTpl(prod); 
console.log(result);
```
```
<dl class="product"><dt>女装</dt><dd>短款</dd<dd>冬季</dd><dd>春装</dd></dl>
```
##写出两种以上声明多行字符串的方法
例如：
```
var str = 'abcdeabcdeabcdeancdeabcdeabcdeabcdeancdeabcdeabcdeabcdeancdeabcdeabcdeabcdeancde'
```

```
+连接运算符
var str = 'abcdeabcdeabcdeancdeabcdeabcdeabcdean'
+'cdeabcdeabcdeabcdean'
+'cdeabcdeabcdeabcdeancde'
//反斜杠，加了反斜杠后，原来写在一行的字符串，可以分成多行，效果与写在同一行完全一样。注意，反斜杠的后面必须是换行符，而不能有其他字符（比如空格），否则会报错
var str = 'abcdeabcdeabcdeancdeabcdeabcdeabcdean\
          cdeabcdeabcdeabcdeancdeabcdeabcdeabcdea\
          ncde'
```
这段字符串很长，如何多行优雅的显示
##补全如下代码,让输出结果为字符串: hello\\饥人谷
```
//因为反斜杠有转义的作用，所以如果要在文中输出反斜杠，需要再反斜杠前面再加一个反斜杠
var str = 'hello\\\\饥人谷'
console.log(str)
```
##以下代码输出什么?为什么
```
var str = 'jirengu\nruoyu'
console.log(str.length)  //输出13，因为在字符串中间有个换行符，虽然有12个字母，但是加上换行符就是13个
```
##写一个函数，判断一个字符串是回文字符串，如 abcdcba是回文字符串, abcdcbb不是
```
//回文字符串的特点非常明显
//就是将字符串翻转后与原字符串完全相等
//就是回文字符串
var str='abcdcba'
function judge(str){
	str+="";
	return str===str.split("").reverse().join("")
}
console.log(judge(str))



//charAt（）方法可返回指定位置的字符
//从字符串头部和尾部，逐次向中间检测
//这个效率更高
var str='abcdcba'
function judge(str) {  
   for(var i=0,j=str.length-1;i<j;i++,j--){
   	if(str.charAt(i)!==str.charAt(j)){
   		return false;
   	}
   }
   return true;
}  
console.log(judge(str))
```
##写一个函数，统计字符串里出现出现频率最多的字符
```
  var str='afdgahghsdhskjghksfksghk'
   function count(str){
   	var dict={}
   	for(var i=0;i<str.length;i++){
   		if(dict[str[i]]){
   			++dict[str[i]]
   		}
   		else{
   			dict[str[i]]=1
   		}
   	}
   	console.log(dict)
   	var count=0
   	var maxvalue
   	for(var key in dict){
   		if(dict[key]>count){
   			maxvalue=key  //字母
   			count=dict[key] //次数
   		}
   	}
   	console.log(maxvalue)
   }
   count(str)
```
##toUpperCase()，把my-short-string形式的字符串转化成myShortString形式的字符串，如
```
 var str="my-short-string"
 function change(str){
 	var arr=str.split('')
 	// 首先判断数组第一个字符是否为‘-’，如果是则删除
 	if(arr[0]=='-'){
 		arr.splice(0,1)
 	}
 	// 遍历数组
 	for(var i=0;i<arr.length;i++){
 		// 如果遍历过程中遇到‘-’
 		//则将其删除，由于删除后，下一个字母的index会变成当前
 		//删除了的‘-’的index，所以只需要将当前的转换为大写即可
 		//最后利用join将字母进行拼接
 		if(arr[i]=='-'){
 			arr.splice(i,1);
 			arr[i]=arr[i].toUpperCase()
 		}
 	}
 	console.log(arr.join(''))
 }
 change(str)
```
##写一个 ucFirst函数，返回第一个字母为大写的字符 （***）

```
ucFirst("hunger") == "Hunger"
var str="myshortstring"
 function ucFirst(str){
 	var arr=str.split("");
 	arr[0]=arr[0].toUpperCase();
 	console.log(arr.join(''))
 }
ucFirst(str)
```
##写一个函数truncate(str, maxlength), 如果str的长度大于maxlength，会把str截断到maxlength长，并加上...，如
```
//substring 
var str="hello,this is hunger valley"
function truncate(str,maxlength){
	if(str.length>maxlength){
		var str=str.substring(0,maxlength-1)+"..."
	}
	console.log(str)
}
truncate(str,10)
//substr
```


##什么是 JSON格式数据？JSON格式数据如何表示对象？window.JSON 是什么？
- json(javascript object notation)的缩写是一种用于数据交换的文本格式，目的是取代繁琐的xml。具有书写简单，一目了然，符号javascript原生语法，可以由解释引擎直接处理，不用另外添加解析代码。所以，json迅速被接受，成为es5标准的一部分。
- json对象就是json的值，基本要符合以下规则
复合类型的值只能是数组或对象，不能是函数、正则表达式对象、日期对象。
简单类型的值只有四种：字符串、数值(必须以十进制表示)、布尔值和null
字符串必须使用双引号表示，不能使用单引号
对象的键名必须放在双引号里面
数组或对象最后一个成员的后面，不能加逗号
- json对象字面量是一种简单的描述以及声明方式。其实字面量就是一种简单的描述以及声明方式

##如何把JSON 格式的字符串转换为 JS 对象？如何把 JS对象转换为 JSON 格式的字符串?
- JSON是javascript中的内置对象，提供了JSON.parse()、JSON.stringify()等方法。
```
var obj = {
	"name":"xuhongrui",
	"age":25
}
JSON.stringify(obj);

var str = '{"name":"xuhongrui","age":25}';
JSON.parse(str);
```
##总结
- 单引号字符串的内部，可以使用双引号。双引号字符串的内部，可以使用单引号。
- 多行与转义：如果要在单引号字符串的内部，使用单引号（或者在双引号字符串的内部，使用双引号），就必须在内部的单引号（或者双引号）前面加上反斜杠，用来转义
- 字符串的拼接
- 字符串的截取(str.subStr().str.subString(),str.slice())
- 字符串的替换(str.replace())
- 字符串的查找（str.search(),str.match()）
- 转换成大写:str.toUpperCase()
- 转换成小写：str.toLowerCase()
- str.split() 字符串切割
- parse：把字符串转换为JSON对象
- stringify：把Json对象转换为字符串
## 关于字符串截取
###substr（）方法用于返回一个从指定长度的子字符串
- substr(start,length),start必须，length可选，如果start为负数，则start=str.length+start.
- 2如果end为负数，则转为0.
- 3如果没有指定该参数，则子字符串将延续到字符串的最后
###slice（start，end）方法可从已有的数组中返回选定的元素，
- start必需。规定从何处开始选取。如果是负数，那么它规定从数组尾部开始算起的位置。也就是说，-1 指最后一个元素，
- 2 指倒数第二个元素，以此类推。end	可选。规定从何处结束选取。该参数是数组片断结束处的数组下标。如果没有指定该参数，那么切分的数组包含从 start 到数组结束的所有元素。如果这个参数是负数，那么它规定的是从数组尾部开始算起的元素。

- 返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素。
如果start为负数，则start=str.length+start。
如果end为负数，则end=str.length+end。

### substring 方法

- substring 方法用于提取字符串中介于两个指定下标之间的字符
substring(start,end)
开始和结束的位置，从零开始的索引
参数     描述
- start     必需。一个非负的整数，规定要提取的子串的第一个字符在 stringObject 中的位置。
- stop     可选。一个非负的整数，比要提取的子串的最后一个字符在 stringObject 中的位置多 1。如果省略该参数，那么返回的子串会一直到字符串的结尾。
返回值

- 一个新的字符串，该字符串值包含 stringObject 的一个子字符串，其内容是从 start 处到 stop-1 处的所有字符，其长度为 stop 减 start。
-  说明
substring 方法返回的子串包括 start 处的字符，但不包括 end 处的字符。
如果 start 与 end 相等，那么该方法返回的就是一个空串（即长度为 0 的字符串）。
如果 start 比 end 大，那么该方法在提取子串之前会先交换这两个参数。
如果 start 或 end 为负数，那么它将被替换为 0。








