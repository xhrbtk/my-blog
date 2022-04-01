### babel原理
- parse把代码code 变成 ast
- traverse 遍历ast 进行修改
- generate 把ast变成代码code2
- code ->> ast -->> ast2 --> code2
```
// 举个🌰
import { parse } from "@babel/parser"
import traverse from "@babel/traverse"
import generate from "@babel/generator"
// code ->> ast -->> ast2 -->> code2
const code = `let a = 'let'; let b = 2`
const ast = parse(code, { sourceType: 'module' })
//  code -->> ast
console.log(ast)  // ast 为什么表示源代码 因为是把源代码字符串表示成一个树形结构
// ast -->> ast2
// 将ast 里面所有变量声明的let 转换为 var 
// 如果采用正则 那么难以区分 变量声明的let 和 值'let'  
// 在将代码转换为ast以后 可以遍历ast 根据 node.type 去判断  是否为variableDeclaration （变量声明）
traverse(ast, {
    enter: item => {
       if( item.node.type  ==  'VariableDeclaration'){
           if(item.node.kind === 'let'){
               item.node.kind = 'var'
           }
       }
    }
})
//  将最新的ast 转换为代码
// ast2 -->> code2
const result = generate(ast, {}, code)
console.log(result.code)
```

## 为什么要用ast 
- 很难用正则表达式来替换
- 需要识别每个单词的意思 才能做到只修改用于声明变量的let
- 而ast可以明确的告诉你每个let 的意思

### babel工具
- babel 可以把高级代码翻译成ES5
- @babel/parser
- @babel/traverse
- @babel/generator
- @babel/core 包含前三者
- @babel/preset-env 内置很多规则
- 如果使用babel/core 则上面的🌰可以变为下面的形式
```
import { parse } from "@babel/parser"
import * as babel from '@babel/core'

const code = `let a = 'let'; let b = 2; const c = 3`
const ast = parse(code, { sourceType: 'module' })

const result = babel.transformFromAstSync(ast, code, {
    presets: ['@babel/preset-env']
})
console.log(result.code)
```

### 循环依赖
- 有的循环依赖可以正常执行
- 有的循环依赖不可以
- 但都可以做静态分析