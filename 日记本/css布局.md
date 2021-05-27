###常见布局（pc）
- 固定宽度布局
- 弹性布局
- 响应式布局-----多终端（pc/pad/phone）
###定宽
width与max-width区别
###两列布局
一列固定宽度，另一列自适应宽度
两列都是固定宽度
###浏览器渲染先后顺序
aside应该在main的上面，因为main是一个普通流元素，它会把整行空间沾满，aside有浮动，只能往下靠边站。
![image.png](http://upload-images.jianshu.io/upload_images/8649258-1982ea3e50ea2452.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/8649258-cd1dd30ffef94626.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###三列布局
- 两侧两列固定宽度，中间列自适应宽度
- 把左浮动和右浮动的元素放前面
###css浮动和负边距、圣杯布局
- 浮动  vs  负margin
对于相邻的两个浮动元素，如果因为空间不够导致第二个浮动元素下移，可以通过给第二个浮动元素设置margin-left：负值来让第二个元素上移，其中负值大于等于元素上移后和第一个元素重合的临界值
- 水平等距排列布局
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>排列布局</title>
</head>
<style>
	
	ul,li{
		margin: 0;
		padding: 0;
		list-style: none;
	}
	.ct{
		overflow: hidden;
		width: 640px;
		border: 1px solid red;
		margin: 0 auto;
	}
	.ct .item{
		float: left;
		width: 200px;
		height: 200px;
		background: green;
		margin-left: 20px;
		margin-top: 20px;
	}
	.ct>ul{
		margin-left: -20px;
	
	}
</style>
<body>
	<div class="ct">
		<ul>
			<li class="item">1</li>
			<li class="item">2</li>
			<li class="item">3</li>
			<li class="item">4</li>
			<li class="item">5</li>
			<li class="item">6</li>
			<li class="item">7</li>
			<li class="item">8</li>
		</ul>
	</div>
</body>
</html>
```
###圣杯布局
- 是三列布局，两边固定宽度，中间自适应
- 中间内容元素在dom元素次序中优先位置
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>圣杯布局</title>
</head>
<style>
.content:after{
	content: '';
	display: block;
	clear: both;
}
	.content{
		padding-left: 110px;
		padding-right: 160px;
	}
	.aside{
		width: 100px;
		height: 300px;
		background: red;
		float: left;
		margin-left: -100%;
		position: relative;
		left: -100px;
	}
	.extra{
		width: 150px;
		height: 300px;
		background: yellow;
		float: left;
		margin-left: -150px;
		position: relative;
		right: -150px;
	}
	.main{
		height: 400px;
		background: blue;
		float: left;
		width: 100%;

	}

</style>
<body>
	<div class="content">
		<div class="main">main</div>
		<div class="aside">aside</div>	
		<div class="extra">extra</div>
	</div>
	
</body>
</html>
```
###双飞翼布局
- 双飞翼布局与圣杯布局相同，都是左右宽度固定，中间自适应
如果把三栏布局比作一只大鸟，可以把main看成是鸟的身体，sub和extra则是鸟的翅膀。这个布局的实现思路是，先把最重要的身体部分放好，然后再将翅膀移动到适当的地方.

其实跟上边的圣杯布局差不多的，当然也可以改动一下（自己想想有哪些不同吧）

恩，这里有一只鸟~

左翅sub有200px,右翅extra..220px.. 身体main自适应未知

1.html代码中，main要放最前边，sub  extra

2.将main  sub  extra 都float:left

3.将main占满 width:100%

4.此时main占满了，所以要把sub拉到最左边，使用margin-left:-100%  同理 extra使用margin-left:-220px

（这时可以直接继续上边圣杯布局的步骤，也可以有所改动）

5.main内容被覆盖了吧，除了使用外围的padding，还可以考虑使用margin。

给main增加一个内层div-- main-inner, 然后margin:0 220px 0 200px

6.main正确展示
```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
<title>双飞翼布局</title>
<style type="text/css">
    *{margin: 0;padding: 0;}
    body{min-width: 700px;}
    .header,
    .footer{ 
        border: 1px solid #333;
        background: #aaa;
        text-align: center;
    }
    .sub,
    .main,
    .extra{ 
        float: left;
        min-height: 130px;
    }
    .sub{
        margin-left: -100%;
        width: 200px;
        background: red;
    }
    .extra{
        margin-left: -220px;
        width: 220px;
        background: blue;
    }
    .main{ 
        width: 100%;
    }
    .main-inner{ 
        margin-left: 200px;
        margin-right: 220px;
        min-height: 130px;
        background: green;
        word-break: break-all;
    }
    .footer{ 
        clear: both;
    }
</style>
</head>
<body>
<div class="header">
    <h4>header</h4>
</div>
    <div class="main">
    <div class="main-inner">
        <h4>main</h4>
        <p>HHHHHHHHHHHHHHHHHHHHHH
        hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh
        HHHHHHHHHHHHHHHHHHHHHH
        hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh
        </p>
        </div>
    </div> 
    <div class="sub">
    <h4>sub</h4>
        <p>oooooooooooooo
        00000000000000000
        ooooooooooooooo
        ooooooooooooooo
        000000000000000</p>
    </div>
      <div class="extra">
    <h4>extra</h4>
        <p>BBBBBBBBBBBBBB
        BBBBBBBBBBBBBBBBBB
        88888888888888888888</p>
    </div>
    <div class="footer">
        <h4>footer</h4>
    </div>
</body>
</html>
```
##圣杯布局和双飞翼布局异同
- 二者都是三栏布局
- 二者都是center在前面渲染，left和right随后
- 三部分全部float：left  调整left和right的负margin值
- 不同之处在于，为了避免left和right影响中间文字内容，圣杯布局是采用position：relative定位，双飞翼布局是在center里面加了一个子div，然后为这个子div设置左右margin值。




