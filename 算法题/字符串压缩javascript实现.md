- 通过键盘输入一串小写字母(a~z)组成的字符串。请编写一个字符串压缩程序，将字符串中连续出席的重复字母进行压缩，并输出压缩后的字符串。
压缩规则：
- 仅压缩连续重复出现的字符。比如字符串abcbc由于无连续重复字符，压缩后的字符串还是abcbc
压缩字段的格式为"字符重复的次数+字符"。例如：字符串xxxyyyyyyz压缩后就成为3x6yz
```
// 
function compileStr(str){
    let count = 1
    let newStr = ''
    for(let i =0; i < str.length -1; i++){
        if(str[i] == str[i+1]){
            count ++
            countinue   // 如果此时的字符和后一个字符想等的话 那么跳出此次循环 继续下次循环
        }else{
            if(count == 1){    
                newStr += str[i]
            }else{
                newStr += count + str[i]
                count = 1
            }
        }
    }
    return newStr
}
```
