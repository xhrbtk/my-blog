```
//$axios,是在main.js 里对axios进行了全局挂载
import axios from 'axios'
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded'
axios.defaults.withCredentials = true
axios.defaults.transformRequest = function (data) {
  return Qs.stringify(data)
}
Vue.prototype.$axios = axios
```
- get请求
```
export function get (url, params) {
  return new Promise((resolve, reject) => {
    this.$axios.get(url, {
      params: params
    }).then(response => {
      resolve(response.data)
    }).catch(err => {
      reject(err)
    })
  })
}
```
- post请求
```
export function post (url, data) {
  return new Promise ((resolve, reject) => {
    this.$axios.post(url, data).then(response => {
      resolve(response.data)
    }).catch(err => {
      reject(err)
    })
  })
}
```
- 在main.js中引入
```
import {get, post} from '@/assets/js/until.js'
//挂载在vue
Vue,prototype.$get = get
Vue.prototype.$post = post
```
- 在组件中使用
```
this.$get(url, params).then((response) => {
  console.log(response)
}).catch(err => {
  this.$message.error('网络繁忙')
})
```
