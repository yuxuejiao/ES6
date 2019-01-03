###ES6常用语法总结
- ES6简介
    - ECMAScript 和 JavaScript 的关系   
        ECMAScript是标准。ECMAScript是JavaScript的规格，JavaScript是ECMAScript的实现。
    - ES6   
        ES6是一个泛指，含义是5.1版本以后的JavaScript的下一代标准，涵盖了ES2015、ES2016、ES2017 等等。   
- Babel转码器   
    将ES6代码转换为ES5代码。     
- Babel-polyfill   
    Babel默认只转换新的JavaScript句法（syntax），而不转换新的API。比如：Iterator、Generator、Set、Map、Proxy、Reflect、Symbol、Promise等全局对象，以及一些定义在全局对象上的方法（比如Object.assign）都不会转码。
    此时必须使用babel-polyfill，为当前环境提供一个垫片。    
    install：npm install --save babel-polyfill   
    import: 在脚本头部，加入 import "babel-polyfill"   
- let 和 const
    - 1、不存在变量提升，即变量在声明之前是不能使用的。
    - 2、暂时性死区：只要块级作用域内存在let命令，它所声明的变量就“绑定”（binding）这个区域，不再受外部的影响。      
       ```
              var tmp = 123;   
              if (true) {  
                tmp = 'abc'; // ReferenceError
                let tmp;
              }   
       ```
     - 3、不允许在同一作用域内重复声明同一个变量
     - 4、带来了块级作用域（ES5只有全局作用域和函数作用域）
          -  外层作用域无法读取内层作用域的变量
          -  内层作用域可以定义外层作用域的同名变量
     - 5、const声明常量，一旦声明，就要立即初始化。     
     - 6、顶层对象（在浏览器环境，顶层对象指的是window对象）的属性   
        在ES5中，顶层对象的属性等价于全局变量。   
        在ES6中，var，function声明的全局变量是顶层对象的属性，但是let,const,class命令声明的变量，不属于顶层对象的属性。
        ```
        var a = 1;
        // 如果在 Node 的 REPL 环境，可以写成 global.a
        // 或者采用通用方法，写成 this.a
        window.a // 1
        
        let b = 1;
        window.b // undefined
        ```
- 变量的解构赋值   
    解构：从数组和对象中提取值，对变量进行赋值。   
    - 数组的解构赋值  
    `let [a, b, c] = [1, 2, 3];`   
    解构赋值允许指定默认值：   
    `let [x, y = 'b'] = ['a']; // x='a', y='b'`
    - 对象的解构赋值   
    `let { foo, bar } = { foo: "aaa", bar: "bbb" };`   
    如果变量名与属性名不一致，必须写成下面这样   
    `let { foo: baz } = { foo: 'aaa', bar: 'bbb' };
     baz // "aaa"`   
     foo是匹配的模式，baz才是变量。真正被赋值的是变量baz，而不是模式foo。   
     对象的解构也可以指定默认值：   
     `var {x: y = 3} = {x: 5};
      y // 5`
     - 字符串的解构赋值   
     ```
     const [a, b, c, d, e] = 'hello';
      a // "h"
      b // "e"
      c // "l"
      d // "l"
      e // "o"
     ```        
     - 函数参数的解构赋值
     ```
     function add([x, y]){
       return x + y;
     }
     
     add([1, 2]); // 3
     ```
     函数参数也可以指定默认值
- 变量解构赋值用途
    - 交换变量的值
    ```
    let x = 1;
    let y = 2;
    
    [x, y] = [y, x];
    ```
    - 从函数返回多个值：函数只能返回一个值，如果要返回多个值，就必须放在数组或对象里。而解构则为调用函数后的取值提供了很大的方便。
   
    ```
    // 返回一个数组
    
    function example() {
      return [1, 2, 3];
    }
    let [a, b, c] = example();
    
    // 返回一个对象
    
    function example() {
      return {
        foo: 1,
        bar: 2
      };
    }
    let { foo, bar } = example();
    ```          
    - 函数参数的定义和初始化：解构赋值很方便将一组参数与变量名对应起来，并且设定默认值
    ```
    // 参数是一组有次序的值
    function f([x = 0, y = 1, z = 2]) { ... }
    f([1, 2, 3]);
    
    // 参数是一组无次序的值
    function f({x = 0, y = 1, z = 2}) { ... }
    f({z: 3, y: 2, x: 1});
    ```
    - 提取JSON数据
    ```
    let jsonData = {
      id: 42,
      status: "OK",
      data: [867, 5309]
    };
    
    let { id, status, data: number } = jsonData;
    ```
    - 遍历map结构
    ```
    for (let [key, value] of map) {
      console.log(key + " is " + value);
    }
    ```
    