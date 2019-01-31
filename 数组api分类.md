- 检测是否为数组      
  Array.isArray(arr) 返回true或false
- 迭代   
  参数是回调函数，对数组中的每一项运行给定函数   
  every：如果函数对每一项都返回true,则返回true   
  some：如果任一项返回true,则返回true   
  forEach：该方法没有返回值   
  map：返回每次函数调用结果组成的数组   
  filter：会返回由true的项组成的数组  
  
  ----
  for...of：for(let item of arr) 
  
- 归并   
  reduce：接收一个函数作为参数，这个函数有四个参数：previousValue,currentValue,index,array。返回一个将被叠加到累加器的值。   
  ```
    numbers.reduce((pre,cur,index,arr)=>{
      return pre + cur;
    })
  ```
- 复制   
    Array.from(arr) 返回新数组    
    扩展运算符：将一个数组转为用逗号分隔的参数序列。      
    ``` const arr = [...arr1]    ```     
- 合并        
    concat: arr1.concat(arr2) 返回新数组    
    扩展运算符：const arr = [...arr1, ...arr2]   
- 修改   
    slice(startIndex, endIndex-1)：返回截取的新数组。当只有一个参数时，表示从startIndex位置开始截取，一直到数组末尾。      
    splice: 修改原数组，返回删除的项   
     删除：splice(startIndex, delCount)   
     插入：splice(startIndex, 0(要删除的项数), 要插入的项)   
     替换：splice(startIndex, delCount, 要插入的任意数量的项)   
- 排序      
  reverse     
  sort    
- 查找   
  返回要查找的项在数组中的位置，找不到返回-1：   
  indexOf：从数组的开头开始查找   
  lastIndexOf：从数组的尾部开始查找 
  
  ----
  
  参数是回调函数   
  find：返回第一个符合条件的项，没有返回undefined   
  findIndex：返回第一个符合条件的项的索引值，没有返回-1  
  
  ----
  
  includes：查找数组里是否存在某项，返回true或者false   
- Array to String   
  toString()：默认返回以逗号分隔的字符串   
  join   
- 实现栈（后进先出）   
  push / pop   
- 实现队列（先进先出）   
  push / shift    
