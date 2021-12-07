---
title: 数组常用方法
date: 2021-12-06 16:32:34
tags:
---

> 考虑到日常开发中使用比较频繁，为了方便查找与回顾，整理此文。

# [#](#) 基础篇

| 方法          | 描述                                               |
| ------------- | -------------------------------------------------- |
| concat()      | 连接两个或多个数组，并返回已连接数组的副本。       |
| copyWithin()  | 将数组中的数组元素复制到指定位置或从指定位置复制。 |
| entries()     | 返回键/值对数组迭代对象。                          |
| every()       | 检查数组中的每个元素是否通过测试。                 |
| fill()        | 用静态值填充数组中的元素。                         |
| filter()      | 使用数组中通过测试的每个元素创建新数组。           |
| find()        | 返回数组中第一个通过测试的元素的值。               |
| findIndex()   | 返回数组中通过测试的第一个元素的索引。             |
| forEach()     | 为每个数组元素调用函数。                           |
| from()        | 从对象创建数组。                                   |
| includes()    | 检查数组是否包含指定的元素。                       |
| indexOf()     | 在数组中搜索元素并返回其位置。                     |
| isArray()     | 检查对象是否为数组。                               |
| join()        | 将数组的所有元素连接成一个字符串。                 |
| keys()        | 返回 Array Iteration 对象，包含原始数组的键.       |
| lastIndexOf() | 在数组中搜索元素，从末尾开始，并返回其位置。       |
| map()         | 使用为每个数组元素调用函数的结果创建新数组。       |
| pop()         | 删除数组的最后一个元素，并返回该元素。             |
| push()        | 将新元素添加到数组的末尾，并返回新的长度。         |
| reduce()      | 将数组的值减为单个值（从左到右）。                 |
| reduceRight() | 将数组的值减为单个值（从右到左）。                 |
| reverse()     | 反转数组中元素的顺序。                             |
| shift()       | 删除数组的第一个元素，并返回该元素。               |
| slice()       | 选择数组的一部分，并返回新数组。                   |
| some()        | 检查数组中的任何元素是否通过测试。                 |
| sort()        | 对数组的元素进行排序。                             |
| splice()      | 从数组中添加/删除元素。                            |
| toString()    | 将数组转换为字符串，并返回结果。                   |
| unshift()     | 将新元素添加到数组的开头，并返回新的长度。         |
| valueOf()     | 返回数组的原始值。                                 |
| at()          | 2021.1 新提案，解决方括号的限制，可以输入负数。    |

\[TOC\]

## [#](#) 1.1 求和

### [#](#) 方法一：Array.prototype.forEach()

    var total = 0;
    [1, 2, 3].forEach(function (num) {
      total += num;
    });

1  
2  
3  
4

### [#](#) 方法二：Array.prototype.reduce()

    var total = [1, 2, 3].reduce(function (sum, current) {
      return sum + current;
    }, 0);

1  
2  
3

## [#](#) 1.2 排序

### [#](#) 方法一：sort()

    // 默认是升序
    [1, 2, 3, 4].sort((a, b) => a - b); // [1, 2, 3, 4]
    // 降序
    [1, 2, 3, 4].sort((a, b) => b - a); // [4, 3, 2, 1]

1  
2  
3  
4

### [#](#) 方法二：排序算法

![](https://gblobscdn.gitbook.com/assets%2F-Lm9JtwbhXVOfXyecToy%2F-Lm9KQIJAMvCgJQzErQS%2F-Lm9KSPi7v-ygMtlI6Zr%2Fsort.png?alt=media)

参考文献

- [十大经典排序算法 - Git Book (opens new window)](https://sort.hust.cc/)
- [JavaScript 数据结构与算法之美 - 十大经典排序算法 - 天明夜尽 (opens new window)](https://juejin.cn/post/6844903902484103182 target=)

## [#](#) 1.3 取最大值

### [#](#) 方法一：Math.max()

    Math.max() // -Infinity，即 -∞

    Math.max(Infinity, -Infinity) // Infinity，即 ∞

    Math.max(...[1, 2, 3, 4]) // 4

    Math.max.apply(this, [1, 2, 3, 4]) // 4

    [1, 2, 3, 4].reduce( (prev, cur,curIndex,arr)=> {
     return Math.max(prev,cur);
    },0) // 4

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11

## [#](#) 1.4 判断是否包含某值

### [#](#) 方法一：Array.includes()

    [7, 8, 9].includes(4) // false

1

### [#](#) 方法二：Array.indexOf()

    [7, 8, 9].indexOf(4) // -1 如果存在返回索引
    [7, 8, 9].indexOf(9) // 2

1  
2

### [#](#) 方法三：Array.find()

如果数组中无值返回 undefined

    [7, 8, 9].find((item) => item === 4) // undefined
    [7, 8, 9].find((item) => item === 9) // 9

1  
2

### [#](#) 方法四：Array.findIndex()

如果数组中无值返回-1

    [7, 8, 9].findIndex((item)=> item === 4) // -1
    [7, 8, 9].findIndex((item)=> item === 9) // 2

1  
2

## [#](#) 1.5 某一项设置值

### [#](#) 方法一：Array.splice()

    arr = ['aaa', 'bbbb', 'cccc', 'dddd']
    arr.splice(3, 0, 3)
    arr // ['aaa', 'bbbb', 'cccc', 3, 'dddd']

1  
2  
3

## [#](#) 1.6 每一项设置值

### [#](#) 方法一：Array.fill()

    [7,8,9,10,11,12].fill() // [undefined, undefined, undefined, undefined, undefined, undefined]
    [7,8,9,10,11,12].fill(7) // [7, 7, 7, 7, 7, 7]
    [7,8,9,10,11,12].fill(3, 2, 4) // [7, 8, 3, 3, 11, 12]

1  
2  
3

### [#](#) 方法二：Array.map()

    [7, 8, 9].map((item, idx) => item % 2) // [1, 0, 1]
    [7, 8, 9].map((item, idx) => idx) // [0, 1, 2]

1  
2

## [#](#) 1.7 每一项是否满足

### [#](#) 方法一：Array.every()

    [1,2,3].every(item=>{return item>2}) //false

1

## [#](#) 1.8 有一项满足

### [#](#) 方法一：Array.some()

    [1,2,3].some(item=>{return item>2}) //true

1

# [#](#) 贰。番外篇

## [#](#) 2.1 重写 Array .prototype. at()

    // 兼容老浏览器的 MDN polyfill
    // 注释：Polyfill 是一块代码（通常是 Web 上的 JavaScript），用来为旧浏览器提供它没有原生支持的较新的功能。
    if (Array.prototype.at) {
        Array.prototype.at = function (idx) {
            return this[this.length + idx]
        }
    }
    arr = ['aaa', 'bbbb', 'cccc', 'dddd']
    arr.at(-1) // 'dddd'
    arr.at(-3) // 'bbbb'

1  
2  
3  
4  
5  
6  
7  
8  
9  
10

## [#](#) 2.2 清空数组

### [#](#) 方法一：Array.length

最快

    arr = ['aaa', 'bbbb', 'cccc', 'dddd']
    arr1 = arr
    arr // ['aaa', 'bbbb', 'cccc', 'dddd']
    arr1 // ['aaa', 'bbbb', 'cccc', 'dddd']

    arr.length = 0 // 0

    arr // []
    // 被引用的数组，也会被清空
    arr1 // []

1  
2  
3  
4  
5  
6  
7  
8  
9  
10

### [#](#) 方法二：Array.splice()

    arr = ['aaa', 'bbbb', 'cccc', 'dddd']
    arr1 = arr

    arr.splice(0) // ['aaa', 'bbbb', 'cccc', 'dddd']

    arr // []
    // 同上，被引用的也会被清空
    arr1 // []

1  
2  
3  
4  
5  
6  
7  
8

### [#](#) 方法三：直接赋予新数组\[\]

最慢，且占用内存

    arr = ['aaa', 'bbbb', 'cccc', 'dddd']
    arr1 = arr

    arr = [] // []

    arr // []
    // 被引用的数组，不会被清空
    arr1 // ['aaa', 'bbbb', 'cccc', 'dddd']

1  
2  
3  
4  
5  
6  
7  
8

## [#](#) 2.3 扁平化

    const arr = [1, [2, [3, [4, 5]]], 6];
    // => [1, 2, 3, 4, 5, 6]

1  
2

### [#](#) 方法一：Array.prototype.flat()

    const res1 = arr.flat(Infinity);

1

### [#](#) 方法二：new RegExp()

    // 缺点：都会变成字符串
    const res2 = JSON.stringify(arr).replace(/\[|\]/g, '').split(',');
    // 改良版
    const res3 = JSON.parse('[' + JSON.stringify(arr).replace(/\[|\]/g, '') + ']');

1  
2  
3  
4

### [#](#) 方法三：Array.prototype.reduce()

    const flatten = arr => {
      return arr.reduce((pre, cur) => {
        return pre.concat(Array.isArray(cur) ? flatten(cur) : cur);
      }, [])
    }
    const res4 = flatten(arr);

1  
2  
3  
4  
5  
6

### [#](#) 方法四：函数递归

    const res5 = [];
    const fn = arr => {
      for (let i = 0; i < arr.length; i++) {
        if (Array.isArray(arr[i])) {
          fn(arr[i]);
        } else {
          res5.push(arr[i]);
        }
      }
    }
    fn(arr);

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11

### [#](#) 方法五：while() + some()

    function flatten(arr) {
        while(arr.some(item=>Array.isArray(item))) {
            arr = [].concat(...arr);
        }
        return arr;
    }

1  
2  
3  
4  
5  
6

## [#](#) 2.4 合并

### [#](#) 方法一：Array.push()

    const arr = ['aaa', 'bbbb', 'cccc', 'dddd']
    arr.push(1, 2, 3,[4, 5, 6]) // 8
    arr // ['aaa', 'bbbb', 'cccc', 'dddd', 1, 2, 3, Array(3)]

1  
2  
3

### [#](#) 方法二：Array.concat()

    arr.concat([1, 2, 3],[4, 5, 6]) // ['aaa', 'bbbb', 'cccc', 'dddd', 1, 2, 3, 4, 5, 6]
    arr // ['aaa', 'bbbb', 'cccc', 'dddd']

1  
2

### [#](#) 方法二：扩展运算符

    [...[1, 2, 3, 4],...[4, 5]] //[1,2,3,4,5,6]

1

## [#](#) 2.5 去重

    const arr = [1, 1, '1', 17, true, true, false, false, 'true', 'a', {}, {}];
    // => [1, '1', 17, true, false, 'true', 'a', {}, {}]

1  
2

### [#](#) 方法一：new Set()

    const arr1 = Array.from(new Set(arr));
    // 或
    const arr1 = [...new Set(arr)];

    // 是 Set 类型，不是 Array 类型
    Object.prototype.toString.call(new Set(arr)) // '[object Set]'

1  
2  
3  
4  
5  
6

### [#](#) 方法二：filter() + indexOf()

    const arr2 = arr => {
      return arr.filter((item, index) => {
        return arr.indexOf(item) === index;
      });
    }

1  
2  
3  
4  
5

### [#](#) 方法三：new Map()

    const arr3 = arr => {
      const map = new Map();
      const res = [];
      for (let i = 0; i < arr.length; i++) {
        if (!map.has(arr[i])) {
          map.set(arr[i], true)
          res.push(arr[i]);
        }
      }
      return res;
    }

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11

### [#](#) 方法四：includes()

    const arr4 = arr => {
      const res = [];
      for (let i = 0; i < arr.length; i++) {
        if (!res.includes(arr[i])) res.push(arr[i]);
      }
      return res;
    }

1  
2  
3  
4  
5  
6  
7

## [#](#) 2.6 交集

### [#](#) 方法一：new Set()

    const one = [0, 2, 4, 6, 8, 8]
    const two = [1, 2, 3, 4, 5, 6]
    const duplicated = [...new Set(one)].filter(v => two.includes(v)) // [2, 4, 6]

1  
2  
3

## [#](#) 2.7 删除虚值

### [#](#) 方法一：Array.prototype.filter()

    const arr = [0, 'blue', '', NaN, 9, true, undefined, 'while', false]
    const real = arr.filter(Boolean) // ['blue', 9, true, 'while']

1  
2

## [#](#) 2.8 重组（变量交换）

### [#](#) 方法一：解构赋值

    arr = ['aaa', 'bbbb', 'cccc', 'dddd', 'eee', 'fff']
    [arr[1], arr[2]] = [arr[2], arr[1]] // ['cccc', 'bbbb']
    arr // ['aaa', 'cccc', 'bbbb', 'dddd']

    // 如果想获取单个值
    [a, , , e, f] = arr
    a // 'aaa'
    e // 'dddd'
    f // 'eee'

1  
2  
3  
4  
5  
6  
7  
8  
9

### [#](#) 方法二：Array.splice()

    arr = ['aaa', 'bbbb', 'cccc', 'dddd', 'eee', 'fff', 'ggg', 'hhh', 'iii']
    arr.splice(1, 3, ...arr.splice(4, 4, arr[1], arr[2], arr[3])) // ['bbbb', 'cccc', 'dddd']
    arr // ['aaa', 'eee', 'fff', 'ggg', 'hhh', 'bbbb', 'cccc', 'dddd', 'iii']

1  
2  
3

### [#](#) 方法三：引入中转变量

    temp = arr[1]
    arr[1] = arr[2]
    arr[2] = temp

1  
2  
3

## [#](#) 2.9 类数组 --> 数组

    // 类数组（包含 length 属性，比如 arguments、DOM 操作方法返回的结果等）
    const asArr = { 0: 'aaa', '1': 'bbb', '二': 'ccc', 4: 'eee', length: 6 }

1  
2

### [#](#) 方法一：Array.prototype.from()

    Array.from(asArr)
    // => ['aaa', 'bbb', undefined, undefined, 'eee', undefined]
    // undefined 可枚举

1  
2  
3

### [#](#) 方法二：Array.prototype.slice.call()

    Array.prototype.slice.call(asArr)
    // => ['aaa', 'bbb', empty × 2, 'eee', empty]
    // empty 不可枚举

1  
2  
3

PS：其他产生 empty 的情况

    // 也会产生 empty 空位，不会改变 length 属性
    delete arr[2]
    // 直接删掉元素，且改变 length 属性
    arr.splice(2, 1)

1  
2  
3  
4

### [#](#) 方法三：扩展运算符

    [...document.querySelectorAll('div')]

1

## [#](#) 2.10 数组 --> 对象

### [#](#) 方法一：扩展运算符

    arr = ['aaa', 'bbbb', 'cccc', 'dddd']
    // ['aaa', 'bbbb', 'cccc', 'dddd']
    { ...arr }
    // {0: 'aaa', 1: 'bbbb', 2: 'cccc', 3: 'dddd'}

1  
2  
3  
4

### [#](#) 方法二：while()

    i = 0
    s = {}
    arr = ['aaa', 'bbbb', 'cccc', 'dddd']

    while (arr[i]) {
        s[i] = arr[i++]
    }

    s // {0: 'aaa', 1: 'bbbb', 2: 'cccc', 3: 'dddd'}

1  
2  
3  
4  
5  
6  
7  
8  
9

### [#](#) 方法三：Object.fromEntries()

    Object.keys({name:'张三',age:14}) // ['name','age']
    Object.values({name:'张三',age:14}) // ['张三',14]
    Object.entries({name:'张三',age:14}) // [[name,'张三'],[age,14]]
    Object.fromEntries([name,'张三'],[age,14]) // ES10的api,Chrome不支持, firebox输出{name:'张三',age:14}

1  
2  
3  
4

## [#](#) 2.11 浅拷贝

### [#](#) 方法一：Array.slice()

    arr = ['aaa', 'bbbb', 'cccc', 'dddd']
    arr1 = arr.slice(0)
    arr[1] = 2333 // 2333
    arr // ['aaa', 2333, 'cccc', 'dddd']
    arr1 // ['aaa', 'bbbb', 'cccc', 'dddd']

1  
2  
3  
4  
5

### [#](#) 方法二：展开操作符

    arr = ['aaa', 'bbbb', 'cccc', 'dddd']
    arr1 = [...arr]
    arr[1] = 2333 // 2333
    arr // ['aaa', 2333, 'cccc', 'dddd']
    arr1 // ['aaa', 'bbbb', 'cccc', 'dddd']

1  
2  
3  
4  
5

### [#](#) 方法三：Array.concat()

    arr = ['aaa', 'bbbb', 'cccc', 'dddd']
    arr1 = [].concat(array)
    arr[1] = 2333 // 2333
    arr // ['aaa', 2333, 'cccc', 'dddd']
    arr1 // ['aaa', 'bbbb', 'cccc', 'dddd']

1  
2  
3  
4  
5

### [#](#) 方法四：直接赋值

    arr = ['aaa', 'bbbb', 'cccc', 'dddd']
    arr1 = arr
    arr[1] = 2333 // 2333
    arr // ['aaa', 2333, 'cccc', 'dddd']
    arr1 // ['aaa', 2333, 'cccc', 'dddd']

1  
2  
3  
4  
5

## [#](#) 2.12 Array.from 达到 .map 的效果

    arr = [
        { name: '张三', age: 18 },
        { name: '李四', age: 18 },
        { name: '王麻子', age: 18 },
        { name: '小六', age: 18 },
    ]
    nameMap = arr.map(v => v.name) // ['张三', '李四', '王麻子', '小六']
    nameMap = Array.from(arr, ({name}) => name) // ['张三', '李四', '王麻子', '小六']

1  
2  
3  
4  
5  
6  
7  
8

## [#](#) 2.13 获取最后 n 个元素

### [#](#) 方法一：Array.splice()

    arr = ['aaa', 'bbbb', 'cccc', 'dddd']

    arr.slice().splice(-1) // ['dddd']
    arr.slice().splice(-3) // 'bbbb', 'cccc', 'dddd'

1  
2  
3  
4

## [#](#) 2.233 二维数组绘制图形

### [#](#) 方法一：Emmm

    // Emmmm

1

# [#](#) 弎。循环的性能与小优化

## [#](#) 优化一：优化 for 循环

- 当循环复杂度为 `O(n)` 时，`减少每次迭代的工作量`是最有效的方法。
- 当复杂度大于 `O(n)` 时，建议着重`减少迭代次数`。

### [#](#) a. 减少每次取 length 的次数

这样避免了每次执行循环都要先去找 array.length

    for (let i = 0; i < array.length; i++) {
        console.log(i) // 0 1 2
    }

    // 优化后
    for (let i = 0, len = array.length; i < len; i++) {
        console.log(i) // 0 1 2
        // do sth...
    }

1  
2  
3  
4  
5  
6  
7  
8  
9

### [#](#) b. 倒序循环

    for (let i = array.length; i > 0; i--) {
        console.log(i) // 3 2 1
    }

    // 优化后
    for (let i = array.length - 1; i >= 0; i--) {
        console.log(i) // 2 1 0
    }

    // 优化后
    for (let i = array.length; i--;) {
        console.log(i) // 2 1 0
        // do sth...
    }

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14

## [#](#) 优化二：不要使用 for-in 来遍历数组

在 JavaScript 提供的循环类型中，只有 for-in 循环比其他几种明显要慢。

由于每次迭代操作会同时搜索实例或原型属性，for-in 循环的每次迭代都会产生更多开销，所以比其他循环类型要慢。

因此，除非你明确需要迭代一个属性数量未知的对象，否则应避免使用 for-in 循环。

## [#](#) 优化三：慎用基于函数的迭代

例如：forEach

基于函数的迭代提供了一个更为便利的迭代方法，但它仍然比基于循环的迭代`要慢一些`。`对每个数组调用外部方法所带来的开销`是速度慢的主要原因。在所有情况下，基于循环的迭代比基于函数的迭代快`8倍`，因此在运行速度要求严格时，基于函数的迭代不是更好的选择。

## [#](#) 优化四：尽量使用 switch-case 条件语句

除非在`非真既假`的判断中，其余条件判断时多用 switch-case 语句，少用 if/else-if/else 语句。原因如下：

- 支持关联操作，即不写 break 语句
- 本质是汇编时生成的跳转表来指示 case 的地址，所以每一个 case 的执行时间基本是相同的，执行效率不会受先后顺序的影响
- 代码更清晰，可读性和可维护性要高很多

## [#](#) 优化五：查找表

当有大量离散数据的时候，使用查找表比使用 if-else 和 switch-case 快得多。

    // 将返回值集合存入数组
    const results = [result0, result1, result2, result3, result4]

    // 返回结果
    return results[value]

1  
2  
3  
4  
5

# [#](#) 肆。课外题

## [#](#) 箭头函数的输出

    var func1 = x => x
    func1(2) // 2
    var func2 = x => {x}
    func2(2) // undefined
    var func3 = x => ({x})
    func3() // {x: undefined}
    func3(2) // {x: 2}

1  
2  
3  
4  
5  
6  
7
