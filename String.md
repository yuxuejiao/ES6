- 字符串的遍历（for...of）
```
for (let codePoint of 'foo') {
  console.log(codePoint)
}
// "f"
// "o"
// "o"
```
- includes()、startsWith()、endsWith() --- 取代ES5中的indexOf 
  - includes()：返回布尔值，表示是否找到了参数字符串。
  - startsWith()：返回布尔值，表示参数字符串是否在原字符串的头部。
  - endsWith()：返回布尔值，表示参数字符串是否在原字符串的尾部。
  ```
    let s = 'Hello world!';
    s.startsWith('Hello') // true
    s.endsWith('!') // true
    s.includes('o') // true
  ``` 
  startsWith()、includes()
  第二个参数表示开始搜索的位置到字符串结尾
  endsWith()
  第二个参数表示从字符串开始位置到指定字符串的最后一个字符一共有几个字符
  ```
  let s = 'Hello world!';
  s.startsWith('world', 6) // true
  s.endsWith('Hello', 5) // true
  s.endsWith('w', 7) // true
  s.includes('Hello', 0) // false
  ```
  - repeat()：返回一个新字符串，表示将原字符串重复n次   
  `'hello'.repeat(2)  // hellohello`   
   参数如果是小数，直接取整。
   - padStart()、padEnd()：在头部或者尾部补全字符串长度，第一个参数是补全后的总长度，第二个参数是用来补全的字符串
   ```
   'x'.padStart(5, 'ab') // 'ababx'
   'x'.padStart(4, 'ab') // 'abax'
   ```
   - matchAll()
   - 模板字符串 --- 取代ES5中的字符串拼接
     用反引号包围，将变量和运算包在${}里面
     
   
