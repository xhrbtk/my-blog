```
//在index.html里面引入weixin
  <script src="http://res.wx.qq.com/open/js/jweixin-1.0.0.js"></script>
//在工具函数里面定义并导出
export function initWeixinSdk(third_app_id) {
  let p = new Promise(resolve => {
    this.$axios.get(this.$httpConfig.HERA_HOST + '/api/hera/wx-third/get-sign-info/',{
      params: {
        appkey: APPKEY,
        third_app_id: third_app_id,
        url: window.location.href
      }
    }).then((res) => {
      if (res.data.code != this.ERRORCODE.SUCCESS) {
        this.$messagebox('获取签名失败！')
        return;
      }
      // weixin sdk初始化功能
      var jsApiList = ["scanQRCode", "onMenuShareTimeline", "onMenuShareAppMessage", "hideMenuItems", "getLocation"];
      // 初始化微信sdk，一次就好，下面的参数是必须的
      wx.config({
        debug: false,
        appId: res.data.appid,          // appid
        timestamp: res.data.timestamp,  // 时间戳
        nonceStr: res.data.noncestr,    // 随机字符串
        signature: res.data.sign,       // 签名
        jsApiList: jsApiList
      })
      // 初始化成功后，这里会自动回调
      wx.ready(() => {

        // 注册成功后，发送`weixinSDKReady`事件
        if (this.ENABLE_WEIXIN_LOCATION) {
          let _this = this
          wx.getLocation({
            type: 'gcj02', // 默认为wgs84的gps坐标，如果要返回直接给openLocation用的火星坐标，可传入'gcj02'
            success(res){
              _this.lat = res.latitude; // 纬度，浮点数，范围为90 ~ -90
              _this.lon = res.longitude; // 经度，浮点数，范围为180 ~ -180。
              resolve()
            },
            cancel(){
              setTimeout(() => {
                _this.$messagebox('未获取到位置信息，请刷新重试')
              }, 1500);
            },
            fail(){
              setTimeout(() => {
                _this.$messagebox('未获取到位置信息，请刷新重试')
              }, 1500);
            }
          });
        }
        // let menuList = [
        //   'menuItem:editTag',
        //   'menuItem:delete',
        //   // 'menuItem:copyUrl',
        //   'menuItem:originPage',
        //   'menuItem:openWithQQBrowser',
        //   'menuItem:openWithSafari',
        //   'menuItem:share:facebook',
        //   'menuItem:share:QZone',
        //   'menuItem:share:qq',
        //   'menuItem:share:weiboApp',
        //   'menuItem:share:email'
        // ];
        // if (ENABLE_WEIXIN_HideMenuItems){
        //   menuList = menuList.concat([
        //     'menuItem:share:appMessage',
        //     'menuItem:share:timeline',
        //     'menuItem:favorite',
        //     'menuItem:share:brand'
        //   ])  // 要显示的菜单项，所有menu项见附录3
        // }
        // wx.hideMenuItems({
        //   menuList: menuList
        // });
      })
    }).catch(err => {
      this.$messagebox('网络繁忙，请稍后再试...')
    })
  })
  return p
}
// 微信sdk   在需要的组件的mounted里面调用
    this.initWeixinSdk()
      wx.ready(() => {
        wx.onMenuShareTimeline({
          title: '创客纵横 智逐未来', // 分享标题$('title').text()
          link: this.$httpConfig.MM_HOST + '/hanhai?channel_code=' + this.channel_code, // 分享链接，该链接域名必须与当前企业的可信域名一致
          desc: '2019中国移动行业智能创客马拉松大赛',
          imgUrl: this.$httpConfig.MM_HOST + '/static/image/customize/hanhai/share.jpg', // 分享图标
          success: function () {
            // MessageBox('恭喜您，分享成功')
          },
          cancel: function () {
            // 用户取消分享后执行的回调函数
            // MessageBox('很遗憾，您已取消分享')
          }
        });
        wx.onMenuShareAppMessage({
          title: '创客纵横 智逐未来', // 分享标题$('title').text()
          link: this.$httpConfig.MM_HOST + '/hanhai?channel_code=' + this.channel_code, // 分享链接，该链接域名必须与当前企业的可信域名一致
          desc: '2019中国移动行业智能创客马拉松大赛',
          imgUrl: this.$httpConfig.MM_HOST + '/static/image/customize/hanhai/share.jpg', // 分享图标
          success: function () {
            // MessageBox('恭喜您，分享成功')
          },
          cancel: function () {
            // 用户取消分享后执行的回调函数
            // MessageBox('很遗憾，您已取消分享')
          }
        });
      })
```
