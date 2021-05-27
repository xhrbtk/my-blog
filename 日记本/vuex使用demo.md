本文仅用于记录学习过程。
由于目前做的项目在公共数据的使用上要求比较低，一般的父子传值就可以解决掉大多数的传值问题。今天有兴趣看了下vuex文档，然后试做了一个小demo。
- 首先是vux的安装，官方文档已经给出了。我使用的是npm方式
```
npm install vuex --save
```
- 安装成功之后，在src下面见文件夹命名为store，并在store下面新建一个名为index.js的文件
![image.png](https://upload-images.jianshu.io/upload_images/8649258-46358d723ca32627.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- store 文件夹下面的index.js中 
```
import Vue from 'vue'
import vuex from 'vuex'
Vue.use(vuex)



export default new vuex.Store({
  state: {
    city: '上海'
  },
  actions: {
    changeCity (ctx, val){
      console.log(val)  //val是dispatch派发传递过来的值
      console.log(ctx)  //ctx是上下文，必传
      ctx.commit('changeCity', val)
    }
  },
  mutations: {
    changeCity (state, val){
      console.log(state)  //state  必传
      console.log(val)  // 要更改的值
      state.city = val
    }
  }
})
```
- 在建好文件之后，在main.js中进行注册
```
import store from '/@store'
new Vue({
  el: '#app',
  router,
  store,
  components: { App },
  template: '<App/>'
})
```
- 前面的都进行之后，接下来就要开始进入正题
```
<!--父组件中引入子组件-->
<template>
  <div >
    <div style="margin:100px 0 0 100px">
      {{$store.state.city}}
    </div>
    <test1></test1>
  </div>
</template>

<script>
import test1 from '@/components/test1.vue'
export default {
  components:{
    test1,
  },
  created () {
    console.log(this.$store.state)
  }
}
</script>
<!--子组件-->
<template>
  <div style="margin:100px 0 0 100px;cursor:pointer">
    <div>这是子组件</div>
    <div @click="changeCityClick">{{$store.state.city}}</div>
  </div>
</template>

<script>
export default {
  data () {
    return {

    }
  },
  methods : {
    changeCityClick () {
      this.$store.dispatch('changeCity', '北京')
    }
  }
}
</script>
```
- 我们在test组件中使用了子组件test1，test和test1 有着同样的数据，如果想要达到修改了子组件的值之后，父组件的值也被修改，我们可以使用父子传值的方式，我们还可以使用vuex实现数据共享。在子组件中点击之后将要改变的值通过派发的方式传递给actions，然后actions通过commit的方式调用mutations去更改state里面的值，这样就达到了父子组件的值的同时变化，如果没有大量的异步操作，可以省略掉actions，直接用commit的方式去将要更改的值传递给mutations，然后mutaitions将state里面的值进行更改，代码如下：
```
//父组件不变
<!--子组件-->
<template>
  <div style="margin:100px 0 0 100px;cursor:pointer">
    <div>这是子组件</div>
    <div @click="changeCityClick">{{$store.state.city}}</div>
  </div>
</template>

<script>
export default {
  data () {
    return {

    }
  },
  methods : {
    changeCityClick () {
      this.$store.commit('changeCity', '北京')  //由dispatch更改成为commit
    }
  }
}
</script>
//store里index.js的修改如下

import Vue from 'vue'
import vuex from 'vuex'
Vue.use(vuex)

export default new vuex.Store({
  state: {
    city: '上海'
  },
//将之前的actions删除掉
  mutations: {
    changeCity (state, val){
      state.city = val
    }
  }
})
```




