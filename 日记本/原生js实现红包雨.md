```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<style>
  .ss{
      width: 20px;
      height: 30px;
      display: inline-block;
      position: absolute;
      top: 0;
      left: 0;
      background-image: url();
      background-repeat: no-repeat;
      background-size: contain;
    }
</style>
<body>
  <script>
    setInterval(() => {
        let height = document.documentElement.clientHeight;
        let width = document.documentElement.clientWidth;
        let top = 0;
        let span = document.createElement('span');
        let arr_img = ['./1.png', './2.png', './3.png', './4.png']
        span.style.left = parseInt(Math.random() * (width - 10)) + 'px'
        span.style.backgroundImage = 'url(' + arr_img[Math.floor(Math.random()*4)] + ')'
        span.className = 'ss'
        document.getElementsByTagName('body')[0].appendChild(span);
        let ss = setInterval(() => {
          if (top > height) {
            window.clearInterval(ss)
            span.parentNode.removeChild(span);
          }
          top += 6;
          span.style.top = top + 'px';
        }, 60);
      }, 1000);
  </script>
</body>
</html>
```
