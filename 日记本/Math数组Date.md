- 写一个函数，返回从min到max之间的 随机整数，包括min不包括max 
```
//包括min，不包括max
function random(a,b){
	return a+Math.floor(Math.random()*(b-a))
}
//如果是不包括min，包括max
function random(a,b){
	return a+Math.ceil(Math.random()*(b-a))
}
```
- 写一个函数，返回从min都max之间的 随机整数，包括min包括max 
```
function random(a,b){
	return a+Math.floor(Math.random()*(b-a+1))
}
```
- 写一个函数，生成一个长度为 n 的随机字符串，字符串字符的取值范围包括0到9，a到 z，A到Z。
```
//得到一个包含a不包含b的随机数
function random(a,b){
	return a+Math.floor(Math.random()*(b-a))
}

function getRandStr(len){
  var dict='0123456789abcdefghijklmnopqlstuvwxyzABCDEFGHIJKLMNOPQLSTUVWXYZ'
	var str=''
	for(var i=0;i<len;i++){
		str+=dict[random[0,62]]
	}
	return str;
}
var str = getRandStr(10); // 0a3iJiRZap
```
-  写一个函数，生成一个随机 IP 地址，一个合法的 IP 地址为 0.0.0.0~255.255.255.255
```
function random(a,b){
	return a+Math.floor(Math.random()*(b-a))
}
function getRandIP(){
 var arr=[];
	for(var i=0;i<4;i++){
		arr.push(random(0,256)) //包含255
	}
	return arr.join('.')
}
var ip = getRandIP()
console.log(ip) // 10.234.121.45
```

-  写一个函数，生成一个随机颜色字符串，合法的颜色为#000000~ #ffffff
```
function random(a,b){
	return a+Math.floor(Math.random()*(b-a))
}
//得到一个随机字符串
function getRandColor(){
	var str=''
	for(var i=0;i<3;i++){
		str+=random(0,256).toString(16)
	}
	return '#'+str;
}
var color = getRandColor()
console.log(color)   // #3e2f1b
```

- 数组方法里push、pop、shift、unshift、join、splice分别是什么作用？用 splice函数分别实现push、pop、shift、unshift方法
1.push()方法可以接收任意数量的参数，把他们逐个添加到数组末尾，并返回修改后数组的长度。
2.pop（）方法是从数组末尾移除最后一项，减少数组的length值，然后返回移除的项
3.shift（）移除数组第一项并返回该值，同时将数组长度建议
4.unshift（）在数组的前端添加任意个项并返回新数组的长度
5.join（）方法用于把数组中的所有元素放入一个字符串。元素是通过指定的分隔符进行分隔的。
6.splice()可以实现删除，插入，替换
- 利用splice实现push方法
```
//向数组中添加任意项，并返回新的数组的长度
//push
var arr=[1,2,3,4]
arr.splice(arr.length,0,'color','red')
```
- 利用splice实现pop方法
```
//从数组末尾移除最后一项，并返回移除的项
var arr=[1,2,3,4]
arr.splice(arr.length-1,1)
```
- 利用splice实现shift方法
```
//移除数组第一项并返回该值，同时将数组长度减1
var arr=[1,2,3]
arr.splice(0,1)
```
- 利用splice实现unshift方法
```
var arr=[1,2,4]
arr.splice(0,0,'color','red')
```
##写一个函数，操作数组，数组中的每一项变为原来的平方，在原数组上操作
```
//常规方法
function squareArr(arr){
	for(var i=0;i<arr.length;i++){
		arr[i]=Math.pow(arr[i],2)
	}
	return arr;
}
var arr = [2, 4, 6]
squareArr(arr)
console.log(arr) // [4, 16, 36]
//利用map函数操作
var arr = [2, 4, 6]
var squareArr=arr.map(function(item,index,array){
	return item*item
})
console.log(squareArr)
```
- 写一个函数，操作数组，返回一个新数组，新数组中只包含正数，原数组不变
```
var arr = [3, -1,  2,  '饥人谷', true]

	var filterPositive=arr.filter(function(item,index,array){
		return (item>0)
	})
console.log(filterPositive) //[3, 2]
console.log(arr) //[3, -1,  2,  '饥人谷', true]
```
- 写一个函数getChIntv，获取从当前时间到指定日期的间隔时间
```
function getChIntc(dateStr){
		var targetDate=new Date(dateStr)
		var curDate=new Date()
		var offset=Math.abs(targetDate-curDate)
		//总秒数
		var totalseconds=Math.floor(offset/1000)
		var second=totalseconds%60
		//总分钟
		var totalminute=Math.floor((offset/1000)/60)
		var minutes=totalminute%60
		//总小时
		var totalhours=Math.floor(totalminute/60)
		var hours=totalhours%24
		//总天数
		var totaldays=Math.floor(totalhours/24)
		return totaldays+'天'+hours+'小时'+minutes+'分钟'+second+'秒'

	}
	console.log(getChIntc('2018-02-15'))
```
##把hh-mm-dd格式数字日期改成中文日期
```
function getChsDate(str){
		var chinese=['零','一','二','三','四','五','六','七','八','九','十']
		var arr=str.split('-')
		//年
		var year=arr[0].split('')
		var stryear=''
		for(var i=0;i<year.length;i++){
			stryear+=chinese[parseInt(year[i])]
		}
		//月
		var strmonth=''
		var month=parseInt(arr[1])
		if(month<10){
			strmonth+=chinese[month]
		}
		if(month==10){
			strmonth+=chinese[10]
		}
		if(month>10){
			var number=month-10
			strmonth+=chinese[10]+chinese[number]
		}

		//day
		var day=parseInt(arr[2])
		var strday=''
		//十位数
		var ten=parseInt(day/10)
		var ten1=day%10
	
		//个位数
		var single=day%10
		if(ten!=0&&ten1!=0){
			strday+=chinese[ten]+chinese[10]+chinese[single]
		}
		else if(single!=0){
			strday+=chinese[single]
		}
		else if((ten!=0)&&(ten1==0)){
			strday+=chinese[ten]+chinese[10]
		}

	return stryear+'年'+strmonth+'月'+strday+'日'
		
		
	}
	console.log(getChsDate('2015-08-31'))
```
##写一个函数，参数为时间对象毫秒数的字符串格式，返回值为字符串。假设参数为时间对象毫秒数t，根据t的时间分别返回如下字符串:

刚刚（ t 距当前时间不到1分钟时间间隔）
3分钟前 (t距当前时间大于等于1分钟，小于1小时)
8小时前 (t 距离当前时间大于等于1小时，小于24小时)
3天前 (t 距离当前时间大于等于24小时，小于30天)
2个月前 (t 距离当前时间大于等于30天小于12个月)
8年前 (t 距离当前时间大于等于12个月)
```
function friendlyDate(dateStr){
        var targetDate=new Date(dateStr)
        var curDate=new Date()
        var offset=Math.abs(targetDate-curDate)
        //总秒数
        var totalseconds=Math.floor(offset/1000)
        //总分钟
        var totalminute=Math.floor((offset/1000)/60)
        //总小时
        var totalhours=Math.floor(totalminute/60)
        //总天数
        var totaldays=Math.floor(totalhours/24)
        //总月数
        var totalmonth=Math.floor(totaldays/30)
        //总年
        var totalyear=Math.floor(totalmonth/12)
        //刚刚
        if(totalmonth>=12){
        	return '1年前'
        }
        else if(totalmonth<12&&totaldays>=30){
        	return '2个月前'
        }
        else if(totalhours>=24&&totaldays<30){
        	return '3天前'
        }
        else if(totalhours>=1&&totalhours<24){
        	return '8小时前'
        }
        else if(totalminute>=1&&totalhours<1){
        	return '3分钟前'
        }
        else if(totalminute<1){
        	return '刚刚'
        }
     
    }
 
console.log(friendlyDate('2017-10-1 07:33:00'))
```
####总结
- floor返回小于参数值的最大整数
- ceil返回大于参数值的最小整数
- pow（）
- random（）
