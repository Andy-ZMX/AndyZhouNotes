- push（）：向尾部添加元素

```javascript
var arr = [1, 2]
arr.push(3, 4)

console.log(arr)		//[1, 2, 3, 4]
```

------------

- unshift（）：向头部添加元素

```javascript
var arr = [1, 2]
arr.unshift(8, 9)

console.log(arr)		//[8, 9, 1, 2]
```

------------

- pop（）：从尾部删除1个元素，空数组是继续删除，不报错

```javascript
var arr = [1, 2]
arr.pop()

console.log(arr)		//[1]
```

------------

- shift（）：从头部删除1个元素，空数组是继续删除，不报错

```javascript
var arr = [1, 2]
arr.shift()

console.log(arr)		//[2]
```

------------

- join（）：数组转字符串

```javascript
let arr = ["A", "n", "d", "y"]
let newstr = arr.join("")

console.log(newstr)        //Andy
```

```javascript
let arr = ["A", "n", "d", "y"]
let newstr = arr.join("*")

console.log(newstr)        //A*n*d*y
```

------------

- concat（）：数组合并

```javascript
//数组合并，不会改变现有的数组，会返回一个新的：
let list1 = [1, 2]
let list2 = [3, 4]
let list3 = [5]
let list = list1.concat(list2, list3)

console.log(list)        //[1, 2, 3, 4, 5]
console.log(list1)       //[1, 2]
```

```javascript
//但是：
let list1 = ["11", { name: "Andy", age: 24 }]
let list2 = ["22"]
let list = list1.concat(list2)

list[1].name = "Curry"

console.log(list1)     // ["11", { name: "Curry", age: 24 }]
console.log(list)      // ["11", { name: "Curry", age: 24 }, 22]	对象的值是引用的 会改变
```

------------

- reverse（）：数组反转 

```javascript
let arr = ["A", "n", "d", "y"]
let newstr = arr.reverse()

console.log(newstr)        //["y", "d", "n", "A"]
```

------------

- includes（）：判断数组是否包含某值

```javascript
const arr = ["a", "b", "c"]
arr.includes("a")        //true
arr.includes("z")        //false
```

------------

- at（）：数组查询

```javascript
let arr = ['AAA', 'BBB', 'CCC']
console.log(arr.at(0))         // AAA
console.log(arr.at(-1))        // CCC
console.log(arr.at(3))         // undefined
console.log(arr.at(-5))        // undefined
```

------------

- flat ()：数组铺平

```javascript
// 将数组降一个维度
// 返回一个新数组，对原数组没有影响
const arr = [1, 2, [3, 4, [5, 6]]]
const newarr = arr.flat()

console.log(newarr)     // [1, 2, 3, 4, [5, 6]]
```

```javascript
// 添加 Infinity 参数，将数据直接降到一维
const arr = [['a', 'b'], ['c', ['d', 'e']], { name: 'Andy' }, 99]
const newarr = arr.flat(Infinity)

console.log(newarr)     // ['a', 'b', 'c', 'd', 'e'，{ name: 'Andy' }, 99]
```

------------

- flatMap ()：数组映射处理

```javascript
// 返回一个新数组，对原数组没有影响
let arr = [1, 2, 3, 4]
let newarr = arr.flatMap((item) => [item * 2])

console.log(newarr)        // [2, 4, 6, 8]
```

```javascript
let arr = [1, 2, 3, 4]
let newarr = arr.flatMap((item) => [item, item * 2])

console.log(newarr)        // [1, 2, 2, 4, 3, 6, 4, 8]
```

------------

- filter ()：数组过滤，返回符合条件的全部项

```javascript
// 返回一个新数组，对原数组没有影响
let arr = [
    {
        name: "Andy",
        age: "20"
    },
    {
        name: "Bruce",
        age: "24"
    }
]
let newarr = arr.filter((item) => item.age > 20)

console.log(newarr)     // [{name: "Bruce",age: "24"}]
```

```javascript
// 删掉偶数，只保留奇数：
let arr = [1, 2, 3, 4, 5, 6]
let newarr = arr.filter(function (x) {
	return x % 2 !== 0
})

console.log(newarr)        //[1, 3, 5]
```

```javascript
// 只保留小写字母：
let arr = ["A", "b", "C", "d", "e", "F"]
let newarr = arr.filter((item) => item >= "a" && item <= "z")

console.log(newarr)        //["b", "d", "e"]
```

------------

- find ()：	数组过滤，返回符合条件的第一项

```javascript
let arr = [
  {
    name: 'Andy',
    age: 18
  },
  {
    name: 'Bruce',
    age: 15
  },
  {
    name: 'Curry',
    age: 22
  }
]

let obj = arr.find(item => {
  return item.age > 12
})

console.log(obj)    // {name: 'Andy', age: 18}
```

------------

- every（） 和 some（）：数组属性判断

```javascript
var arr = [
  { name: "苹果", price: 16 },
  { name: "橘子", price: 8 },
  { name: "香蕉", price: 4 },
  { name: "西瓜", price: 12 },
]

// 判断数组中每一条数据的price是否都大于10
var everyResult = arr.every(function (item) {
  return item.price > 10
})

// 判断数组中是否有一条数据的price大于10
var someResult = arr.some(function (item) {
  return item.price > 10
})

console.log(everyResult)     // false
console.log(someResult)      // true
```

```javascript
// 但是 arr 是空的
var arr = []

// 判断数组中 是否任意一条数据 都满足条件
var everyResult = arr.every(function (item) {
  return item > 10
})

// 判断数组中 是否至少有一条数据 满足条件
var someResult = arr.some(function (item) {
  return item > 10
})

console.log(everyResult)     // true
console.log(someResult)      // false
```

------------

- from（）：对象 转 数组

```javascript
// 可以将 部署了Iterator（迭代器）接口的对象 转化为数组
// Map:
    var m = new Map()
    m.set('AAA', 18)
    m.set('BBB', 19)
    m.set('CCC', 20)
	
    console.log(Array.from(m))    //[["AAA", 18],["BBB", 19],["CCC", 20]]
	
	
// Set:
    var s = new Set()
    s.add('AAA')
    s.add('BBB')
    s.add('CCC')
	
    console.log(Array.from(s))    //["AAA", "BBB", "CCC"]
//第二个参数：
    console.log(Array.from(s, (item) => (item + 1)))    //["AAA1", "BBB1", "CCC1"]
```

```javascript
// 可以将伪数组转为真数组
function fn() {
	let list = Array.from(arguments)
	console.log(list)
}
fn("a", "b", "c")
```

------------

- slice（）和 splice（）：数组截取
**slice 数组截取，不会修改数组，而是返回一个子数组：**

```javascript
// 从数组下标3开始截取
let arr = ["A", "B", "C", "D", "E", "F"]
let newarr = arr.slice(3)

console.log(arr)		//["A", "B", "C", "D", "E", "F"]
console.log(newarr)		//["D", "E", "F"]
```

```javascript
// 左闭右开截取[3,5)
let arr = ["A", "B", "C", "D", "E", "F"]
let newarr = arr.slice(3, 5)

console.log(arr)		//["A", "B", "C", "D", "E", "F"]
console.log(newarr)		//["D", "E"]
```

**splice 用于删除数组中的元素，会改变原始数组：**
```javascript
// 删除数组下标3之后的所有元素
let arr = ["A", "B", "C", "D", "E", "F"]
let newarr = arr.splice(3)

console.log(arr)		//["A", "B", "C"]
console.log(newarr)		//["D", "E", "F"]
```

```javascript
// 删除从数组下标3开始的两个元素
let arr = ["A", "B", "C", "D", "E", "F"]
let newarr = arr.splice(3, 2)

console.log(arr)		//["A", "B", "C", "F"]
console.log(newarr)		//["D", "E"]
```

```javascript
// 删除数组第一个元素：
let arr = ["A", "B", "C", "D", "E", "F"]
let newarr = arr.splice(0, 1)

console.log(arr)		//["B", "C", "D", "E", "F"]
console.log(newarr)		//["A"]
```

```javascript
// 删除数组最后一个元素：
let arr = ["A", "B", "C", "D", "E", "F"]
let newarr = arr.splice(arr.length - 1, 1)

console.log(arr)		//["A", "B", "C", "D", "E"]
console.log(newarr)		//["F"]
```

------------

- indexOf（）：数组查询

```javascript
// 该方法可返回某个指定的字符串值在字符串中首次出现的位置，如果没找到则返回-1
let arr1 = ["a", "b", "b", "c", "d", "e"]

console.log(arr1.indexOf("b"))        //1
console.log(arr1.indexOf("z"))        //-1
```

------------

- reduce

```javascript
// 如果没有第二个参数，第一次迭代 accumulator 为 array[0] currentValue 为 array[1]
let count = 0
const sum = [1, 2, 3, 4].reduce(
	(accumulator, currentValue) => {
		count = count + 1
		return accumulator + currentValue
	}
)

console.log(count)  // 3
console.log(sum)    // 1 + 2 + 3 + 4
```

```javascript
// 如果有第二个参数，第一次迭代 accumulator 为 initialvalue currentValue 为 array[0]
let count = 0
const sum = [1, 2, 3, 4].reduce(
	(accumulator, currentValue) => {
		count = count + 1
		return accumulator + currentValue
	}, 0
)

console.log(count)  // 4
console.log(sum)    // 0 + 1 + 2 + 3 + 4
```