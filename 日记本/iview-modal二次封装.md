```<template>
    <div>
        <Modal title="title" v-model="visible" class-name="vertical-center-modal">
            <p>Content of dialog</p>
            <Input v-model="value" placeholder="default size" @on-change="inputChange" />
            <div slot="footer" class="footer">
                <Button size="large" type="primary" @click.native="ok">确定</Button>
                <Button size="large" type="default" @click.native="cancel">取消</Button>
            </div>
        </Modal>
    </div>
</template>

<script>
window.TestModal = {}
export default {
    data() {
        return {
            visible: false,
            title: '',
            value: '',
        }
    },
    methods: {
        ok() {
            this.visible = false
            this.onok(this.value)
        },
        cancel() {
            this.visible = false
            this.oncancel()
        },
        inputChange() {
            this.change(this.value)
        },
    },
    mounted() {
        TestModal.open = options => {
            this.title = options.title
            this.onok = options.onok
            this.oncancel = options.oncancel
            this.visible = true
            this.value = options.value
            this.change = options.change
        }
    },
}
</script>
```
```
app.vue里面注册引入
```
```
//另一个组件中调用
TestModal.open({
                    title: '23',
                    value: this.value,
                    onok: el => {
                        console.log()
                        console.log('点击了确定')
                        console.log(el)
                    },
                    oncancel: () => {
                        console.log('点击了取消')
                    },
                    change: e => {
                        console.log('点击了改变')
                        console.log(e)
                    },
                })
```
