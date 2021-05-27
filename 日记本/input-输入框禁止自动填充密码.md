```
<input type="text"  id="find-verify" placeholder="短信验证码" autocomplete="off" 
readonly 
onfocus="this.removeAttribute('readonly');" onblur="this.setAttribute('readonly',true);">
//autocomplete="off" 是火狐浏览器提出的，但是并不被其他浏览器厂商认可，在谷歌上面这个方法就不生效
//由于自动填充是浏览器的操作，在input框获得onfocus之前设为只读状态，让浏览器的自动填充无法作用。
```
> readonly 
onfocus="this.removeAttribute('readonly');" onblur="this.setAttribute('readonly',true);">
//在input框里面加入以上3行代码就可以解决浏览器对input框的自动填充问题。
//另外由于input框设置了只读状态，所以有可能导致input框的背景色发生变化，可以在css里面利用
```
input[readonly]{
  background-color: #fff !important;
```
