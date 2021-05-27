form标签用于为用户输入创建html表单。表单能够包含input元素，比如文本字段、复选框、单选框、提交按钮等等。表单还可以包含menus、textarea、fieldset、lengend和label元素，表单用于向服务器传输数据。

- 文本域
'''
<form>
用户：
<input type="text" name="user">
</form>
'''
效果如图：
![image.png](http://upload-images.jianshu.io/upload_images/8649258-8e0a2f9e6ef738ef.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 密码域
'''
<form>
密码：
<input type="password" name="password">
</form>
'''
效果如图：
![image.png](http://upload-images.jianshu.io/upload_images/8649258-d8a0f898f28fa8af.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 复选框
'''
<form>
我喜欢自行车：
<input type="checkbox" name="Bike">
<br />
我喜欢汽车：
<input type="checkbox" name="Car">
</form>
'''
效果如图：
![image.png](http://upload-images.jianshu.io/upload_images/8649258-7887b0eab95d269a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 单选按钮
'''
<form>
男性：
<input type="radio" checked="checked" name="Sex" value="male" />
<br />
女性：
<input type="radio" name="Sex" value="female" />
</form>
'''
效果如图：
![image.png](http://upload-images.jianshu.io/upload_images/8649258-f937a4f614ce8172.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 下拉框
'''
<form>
<select name="cars">
<option value="volvo">Volvo</option>
<option value="saab">Saab</option>
<option value="fiat">Fiat</option>
<option value="audi">Audi</option>
</select>
</form>
'''
效果如图：
![image.png](http://upload-images.jianshu.io/upload_images/8649258-c0ac4208bf538bc5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
-  文本域
'''
<textarea rows="10" cols="30">
The cat was playing in the garden.
'''
效果如图：
![image.png](http://upload-images.jianshu.io/upload_images/8649258-8f94e6b9dded3f91.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 按钮
''' 
<form>
<input type="button" value="Hello world!">
</form>
'''
效果如图：

![image.png](http://upload-images.jianshu.io/upload_images/8649258-1223104a5472d713.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 围绕数据的fieldset
'''
<form>
  <fieldset>
    <legend>健康信息</legend>
    身高：<input type="text" />
    体重：<input type="text" />
  </fieldset>
</form>
'''
效果如图：
![image.png](http://upload-images.jianshu.io/upload_images/8649258-3233e05b17cdb61c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)












