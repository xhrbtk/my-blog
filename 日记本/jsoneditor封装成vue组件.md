```
<template>
    <div>
        <div class="jsoneditor-vue"></div>
    </div>
</template>

<script>
import JSONEditor from 'jsoneditor'
import 'jsoneditor/dist/jsoneditor.min.css'
export default {
    props: {
        value: [String, Number, Object, Array],
        expandedOnStart: {
            type: Boolean,
            default: false,
        },
        mode: {
            type: String,
            default: 'code',
        },
        modes: {
            type: Array,
            default: function() {
                return ['tree', 'text', 'code']
            },
        },
    },
    //会在value任一属性发生变化时 触发
    watch: {
        value: {
          //属性发生变化触发handler这个回调
            async handler(val) {
                if (!this.internalChange) {
                    await this.setEditor(val)
                    this.expandAll()
                }
            },
            deep: true,  //监听这个对象中每一个属性的变化
            immediate: true,  //默认立即触发一次
        },
    },
   
    data() {
        return {
            editor: null,
            error: false,
            json: this.value,
            internalChange: false,
            expandedModes: ['tree', 'view', 'form'],
        }
    },
    mounted() {
        let self = this
        let options = {
            mode: this.mode,
            modes: this.modes, // allowed modes
            onChange() {
                console.log('Json editor change')
                try {
                    let json = self.editor.get()
                    self.json = json
                    console.log(json)
                    self.$emit('json-change', json)
                    self.internalChange = true
                    self.$emit('input', json)
                    self.$nextTick(function() {
                        self.internalChange = false
                    })
                } catch (e) {
                    self.$emit('has-error', e)
                }
            },
            onModeChange() {
                self.expandAll()
            },
        }
        this.editor = new JSONEditor(this.$el.querySelector('.jsoneditor-vue'), options, this.json)
        console.log(this.editor.getMode())
    },
    methods: {
        expandAll() {
            if (this.expandedOnStart && this.expandedModes.includes(this.editor.getMode())) {
                this.editor.expandAll()
            }
        },
        async setEditor(value) {
            if (this.editor) this.editor.set(value)
        },
    },
}
</script>
```
