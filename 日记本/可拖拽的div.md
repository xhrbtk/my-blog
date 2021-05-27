```<!DOCTYPE html>
<html>

<head lang="en">
  <meta charset="UTF-8">
  <title>拖动</title>
  <style>
    div{
      border: 1px solid red;
      position: absolute;
      top: 0;
      left: 0;
      width: 100px;
      height: 100px;
    }
  </style>
</head>

<body>
  <div id="xxx"></div>
  <script>

    var dragging = false
    var position = null
    xxx.addEventListener('mousedown', function (e) {
      dragging = true
      position = [e.clientX, e.clientY]
    })
    document.addEventListener('mousemove', function (e) {
      if (dragging === false) { return }
      const x = e.clientX
      const y = e.clientY

      const deltaX = x - position[0] //相对于client移动的位置
      const deltaY = y - position[1] //相对于client移动的位置

      const left = parseInt(xxx.style.left || 0)
      const top = parseInt(xxx.style.top || 0)

      xxx.style.left = left + deltaX + 'px'   //更新坐标位置
      xxx.style.top = top + deltaY + 'px'   //更新坐标位置
      
      position = [x, y]  //更新初始的client位置
    })
    document.addEventListener('mouseup', function (e) {
      dragging = false
    })
  </script>
</body>

</html>
```

```
//移动端可拖拽div
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8" />
  <title></title>
  <style>
    * {
      padding: 0px;
      margin: 0px;
    }

    div{
      width: 100px;
      height: 100px;
      border: 1px solid red;
      position: absolute;
      top: 0;
      left: 0;
      font-size: 20px;
      cursor: pointer;
    }
  </style>
</head>

<body>
  <div id="xxx">开始游戏</div>
  <script>
    var dragging = false;
    var position = [];
    xxx.addEventListener('touchstart', function(e){
      dragging = true
      if(e.touches){
        var el = e.touches[0]
      }else{
        var el = e.target
      }
      position = [el.clientX, el.clientY]
    })

    xxx.addEventListener('touchmove', function(e){
      if(dragging === false) return
      if (e.touches) {
        var el = e.touches[0]
      } else {
        var el = e.target
      }
      var left = e.target.offsetLeft
      var top = e.target.offsetTop

      var x = el.clientX
      var y = el.clientY

      xxx.style.left = left + x - position[0] + 'px'
      xxx.style.top = top + y - position[1] + 'px'

      position = [x, y]
    })

    xxx.addEventListener('touchend', function(e){
      dragging = false
    })




  </script>
</body>

</html>
```
