文章原有链接[文章原有链接](https://blog.csdn.net/benxiaohai888/article/details/80194227)

```
<!doctype html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>div模拟textarea文本域轻松实现高度自适应</title>
	<style>
	h2{
		text-align: center;
		margin:50px auto;
	}
	.test_box {
    width: 400px; 
    min-height: 20px; 
    max-height: 300px;
    _height: 120px; 
    margin-left: auto; 
    margin-right: auto; 
    padding: 3px; 
    outline: 0; 
    border: 1px solid #a0b3d6; 
    font-size: 12px; 
    line-height: 24px;
    padding: 2px;
    word-wrap: break-word;
    overflow-x: hidden;
    overflow-y: auto;

    border-color: rgba(82, 168, 236, 0.8);
	box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1), 0 0 8px rgba(82, 168, 236, 0.6);
}
	</style>
</head>
<body>
	<h2>div模拟textarea文本域轻松实现高度自适应</h2>
	<div class="test_box" contenteditable="true"><br /></div>
</body>
</html>
```
