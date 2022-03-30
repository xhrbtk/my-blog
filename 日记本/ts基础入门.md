 - 声明类型1   在线code 平台 https://www.typescriptlang.org/play
```
type Name = string  // 声明了一个类型叫做Name  此时的Name 等价于 string
const str: Name = 'xhr'    等价于    const str: string = 'xhr'

type Id = string | number      //声明了一个类型叫做Id Id要么是字符串 要么是 number
const id1: Id = '1'
const id2: Id = 2
const id3: Id = true  // 报错 类型Id要求 只能是字符串或者 number 

type xx = string & number  // 错误的写法  简单类型不可以用& 因为没有一个变量 既可以是 字符串 又可以是数字
type User = {
  name: string
  age: number
}
const p: User = { 
    name: 'xhr'  //只声明name 会报错 因为是User类型 要同时声明 name 和 age
    age: 18
}

type User1 = {
    name: string,
    age?: number  // 加？ 表示 age不是必须的
}
const p1: User1 = {
    name:  'xhr'         // 当类型为User1的时候 age 不是必须的 可以只声明name
}

type User2 = {
    readonly id: string | number  // 如果不希望被更改 加上readonly 就可以禁止更改
    name: string
    age: number
}
const p2: User2 = {
    id: 1,
    name: 'xhr',
    age: '18'
}
p2.id = 2 // 报错 此处的id 是只读的

// 还可以声明一些更精确的类型
type Dir = 't' | 'y' | 'z'
const d: Dir = 'x'  // 报错 d 的值只能是  't' 或 'y' 或 'z' 之中的一个

```
- 声明类型2  对象类型的 | 结合
```
type A = {
    t: 'a',
    specialForA: string
}
type B = {
    t: 'b'
    specialForB: number
}

type C = A | B   // 类型C 要么是A 类型 要么是B 类型

const c: C = {
    t: 'a',
   specialForB: 's'   // 报错 当t 的值为'a'的时候 就已经选定是A类型了 
}
const c: C = {
    t: 'a',
    specialForA: 's'   // 正确
}
```
- 声明类型3 对象类型的 & 操作
```
type A = {
    ta: 'a',
    specialForA: string
}
type B = {
    tb: 'b'
    specialForB: number
}

type C = A & B  // 类型C有4个属性的前提是 A和B 的属性都不相同 

const c: C = {
    ta: 'a',
    specialForA: 's',
    tb: 'b',
    specialForB: 34
}
// 或者类型D和E 具有相同属性的值是相同的 这样类型F可以获得3个属性
type D = {
    t: 'a',
    specialForA: string
}
type E = {
    t: 'a'
    specialForB: number
}
type F = D & E
const f: F = {
    t: 'a',
    specialForA: 's',
    specialForB: 34
}
```
- 声明类型4 interface
```
// interface可以描述函数和对象 不可以描述基本类型   
// interface 可以继承
type Work = string
interface Profile {
    readonly id: number | string
    name: string
    age: number
}

interface ProfileWithWork extends Profile {
    work: Work
}
const p1: ProfileWithWork = {
    name: 'xhr',
    age: 18,
    id: 1,
    work: 'home'
}
// 如果继承的不是明确的 可以使用泛型
interface ProfileWithPet<T> extends Profile {
    pet: T
}
const p2: ProfileWithPet<Cat> = {
    name: 'xhr',
    age: 18,
    id: 1,
    pet: 'cat'
}
```