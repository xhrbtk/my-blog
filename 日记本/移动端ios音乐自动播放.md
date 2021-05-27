```
audioAutoPlay(){
    var audio = document.querySelector('#musicStar')
    var play = function(){
      audio.play()
      document.removeEventListener("touchstart",play, false);
    }
    audio.play()
    document.addEventListener("WeixinJSBridgeReady", function () {
      play()
    }, false)
    document.addEventListener('YixinJSBridgeReady', function() {
      play()
    }, false)
    document.addEventListener("touchstart",play, false)
    },
```
