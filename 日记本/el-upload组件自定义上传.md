最近在使用element-ui框架，但是遇到后端同学要求附带参数需要随着文件的变化而变化，然后用el-upload在before-upload钩子里面进行判断更新，但是实际使用的效果不太理想，附带参数总是慢半拍，并不能实时更新，在网上查找之后发现了大家都在使用http-request方法进行自定义上传，这也是element-ui提供的一个方法。下面为大家提供一个小demo方便大家使用。
```

  
  <template>
    <el-upload
      class="upload-demo"
      ref="upload"
      action="https://jsonplaceholder.typicode.com/posts/"
      :http-request="myUpload"
      :on-success="handleSuccess"
      :on-error="handleError"
      :with-credentials="true">
      <el-button slot="trigger" size="small" type="primary" icon="el-icon-document">选取文件</el-button>
      <div slot="tip" class="el-upload__tip">只能上传<b>apk</b>文件，且文件以“<b>版本号_76</b>”命名<br/>若目标文件已上传过，则此环节可略去</div>
    </el-upload>
</template>
  

<script>
  export default {
    data() {
      return {
        action:"https://jsonplaceholder.typicode.com/posts/",
        fileList: [{name: 'food.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}, {name: 'food2.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}]
      };
    },
    methods: {
    //myupload是自定义的上传方法
  //content.onError及content.onSuccess是ele提供的回调函数  如果删掉这些 将会导致在on-success和onError中不能拿到正确的数据
      myUpload(content) {
        console.log(content)
          var form = new FormData();
          form.append("file", content.file);
          console.log(form)
          this.$axios.post(content.action, form).then(res=>{
              if(res.data.code != 0) {
                  content.onError('文件上传失败, code:' + res.data.code)
              } else {
                console.log(res.data)
                  content.onSuccess('文件上传成功！')
              }
          }).catch(error=>{
                if (error.response) {
                      content.onError('文件上传失败,' + error.response.data);
                  } else if(error.request) {
                      content.onError('文件上传失败，服务器端无响应')
                  } else {
                      content.onError('文件上传失败，请求封装失败')
                  }
          });
      },
handleError(response, file, fileList) {
      this.$message.error("上传文件失败");
    },
   handleSuccess(response, file) {
      if(response.code == this.ERRORCODE.SUCCESS){
        this.form.file_path = response.file_path
        this.isPass = true
        this.file_msg = file
        this.$message.success("上传文件成功")
      }else{
        this.$message.success("上传文件失败")
      }
    },

</script>
```
