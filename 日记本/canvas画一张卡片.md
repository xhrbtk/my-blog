- [预览地址](http://xhrbtk.cn/canvas/canvas.html)
```
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>绘制活动海报</title>
</head>
<style>
  #posterCanvas{
  width: 321px;
  height: 516px;
}
</style>

<body>
  <div style="margin: 0 auto; width: 321px;"></div>
    <canvas id="posterCanvas" width="321" height="516" style="margin: 0 auto;"></canvas>
  </div>
  <script type="text/javascript">
    var posterinfo = {
      pointer_bg: './3.jpg',
      logo: './2.png',
      hand: './hand.png',
      qrcodeSrc: './4.png',
      start_time: '2019-03-12 18:54',
      end_time: '2019-03-19 18:54',
      activity_info: '获奖后凭兑奖码联系活动主办单位即可兑奖'
    }
    posterCanvas(posterinfo);
    function posterCanvas(posterinfo) {
        var c = document.getElementById('posterCanvas');
        var ctx = c.getContext("2d");
        c.width = 321;
        c.height = 516;
        // 为了保证图片的清晰度
        var devicePixelRatio = window.devicePixelRatio || 1;
        var backingStoreRatio = ctx.webkitBackingStorePixelRatio ||
          ctx.mozBackingStorePixelRatio ||
          ctx.msBackingStorePixelRatio ||
          ctx.oBackingStorePixelRatio ||
          ctx.backingStorePixelRatio || 1;
        var ratio = devicePixelRatio / backingStoreRatio;
        c.style.width = c.width + "px";
        c.style.height = c.height + "px";
        c.width = c.width * ratio;
        c.height = c.height * ratio;
        ctx.scale(ratio, ratio);
        ctx.translate(0.5, 0.5);
        ctx.lineWidth = 1;

        var img = new Image();
        // 解决图片跨域问题
        img.setAttribute('crossOrigin', 'anonymous');
        img.src = posterinfo.pointer_bg;
        img.onload = function () {
          // 背景图
          ctx.drawImage(img, 0, 0, 325, 516);
          // logo图
          var img0 = new Image();
          img0.setAttribute('crossOrigin', 'anonymous');
          img0.src = posterinfo.logo;
          img0.onload = function () {
            ctx.drawImage(img0, 10, 20, 100, 24);
            // 将占位背景图去掉
          }
          // 圆角填充矩形
          fillRoundRect(ctx, 10, 160, 300, 341, 10, 'rgba(0,0,0,.4)');
          ctx.fillStyle = '#ffde00';
          // 文案
          ctx.lineWidth = 1;//定义线条宽度
          ctx.font = '14px STHeitiSC-Light'
          ctx.fillText("活动详情", 132, 186);
          // 活动时间
          ctx.font = '14px STHeitiSC-Light'
          ctx.fillText("活动时间", 20, 202);
          ctx.fillStyle = '#fff';
          var timetext = posterinfo.start_time + '-' + posterinfo.end_time;
          ctx.fillText(timetext, 20, 222);
          // 活动说明
          ctx.fillStyle = '#ffde00';
          ctx.fillText("活动说明", 20, 242);
          var explaintext = posterinfo.activity_info;
          // 限制文字说明行数
          drawText(ctx, explaintext, 20, 232, 280);
          // 二维码白底
          ctx.fillStyle = "rgba(255,255,255)";  // 设置或返回用于填充绘画的颜色、渐变或模式
          ctx.fillRect(140, 335, 140, 140);
          // 扫描二维码有惊喜
          ctx.fillStyle = '#ffde00';
          ctx.fillText("扫描二维码有惊喜", 20, 401);
          // 小手
          var img1 = new Image();
          img1.setAttribute('crossOrigin', 'anonymous');
          img1.src = posterinfo.hand;
          img1.onload = function () {
            ctx.drawImage(img1, 61, 429, 20, 20);
          }
          // 二维码
          var img2 = new Image();
          img2.setAttribute('crossOrigin', 'anonymous');
          img2.src = posterinfo.qrcodeSrc;
          img2.onload = function () {
            ctx.drawImage(img2, 150, 345, 120, 120);
          }
        }
        return c
      }
      //绘制圆角
      function fillRoundRect(cxt, x, y, width, height, radius, /*optional*/ fillColor) {
        if (2 * radius > width || 2 * radius > height) { return false; }
        cxt.save();
        cxt.translate(x, y);
        drawRoundRectPath(cxt, width, height, radius);
        cxt.fillStyle = fillColor || "#000"; //若是给定了值就用给定的值否则给予默认值
        cxt.fill();
        cxt.restore();
      }
      function drawRoundRectPath(cxt, width, height, radius) {
        cxt.beginPath(0);
        cxt.arc(width - radius, height - radius, radius, 0, Math.PI / 2);
        cxt.lineTo(radius, height);
        cxt.arc(radius, height - radius, radius, Math.PI / 2, Math.PI);
        cxt.lineTo(0, radius);
        cxt.arc(radius, radius, radius, Math.PI, Math.PI * 3 / 2);
        cxt.lineTo(width - radius, 0);
        cxt.arc(width - radius, radius, radius, Math.PI * 3 / 2, Math.PI * 2);
        cxt.lineTo(width, height - radius);
        cxt.closePath();
      }
      // 限制文本显示行数
      function drawText(context, t, x, y, w) {
        var chr = t.split("");
        var temp = "";
        var row = [];
        context.font = "14px STHeitiSC-Light";
        context.fillStyle = "#fff";
        context.textBaseline = "middle";
        for (var a = 0; a < chr.length; a++) {
          if (context.measureText(temp).width < w && context.measureText(temp + (chr[a])).width <= w) {
            temp += chr[a];
          }
          else {
            row.push(temp);
            temp = chr[a];
          }
        }
        row.push(temp);
        // 只显示3行，加...
        for (var b = 0; b < row.length; b++) {
          var str = row[b];
          if (b == 2) {
            str = str.substring(0, str.length - 1) + '...';
          } else if (b >= 3) {
            str = '';
          }
          context.fillText(str, x, y + (b + 1) * 24);
        }
      }
  </script>
</body>
</html>
```
