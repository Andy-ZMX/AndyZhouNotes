可以保存键值对，并且每一项是有顺序的，任何值都可以作为键和值

------------

 **Map 和 Object 的区别：**
- 键的类型：Map 的键可以是任意值，Object 的键只能为 String 和 Symbol
- 意外的键：Map 默认不包含任何键，只包含显式存入的键值对，Object 有原型，因此它包含默认的键（Object.create(null)可以避免）
- 键的顺序：Map 的键值对有先后顺序，Object 的键值对在某些情况下无序
- 迭代遍历：Map 可以循环直接迭代，Object 用 for...in，或者 Object.keys() 等方法
- 大小：Map 有 size 属性，Object 可以用 Object.keys() 返回的数组长度

------------

**Map.prototype.set()**
添加或更新一个键值对,如果没有就添加，如果有就更新
```javascript
var m = new Map()
m.set('AAA', 18)	// 添加
m.set('BBB', 19).set('CCC', 20)	// 链式添加
```
也可以接受一个数组作为参数，该数组的成员是一个个表示键值对的数组
```javascript
var m = new Map([['name', 'Andy'], ['age', 21]])
```

------------


**Map.prototype.get()**
通过key获取value
```javascript
m.get('BBB')	// 19
m.get('DDD')	// undefined
```

------------


**Map.prototype.has()**
判断元素是否存在，如果有就返回true，没有就返回false
```javascript
m.has('BBB')	// true
m.has('DDD')	// false
```

------------


**Map.prototype.delete()**
删除元素，如果有就删除返回ture，没有就不动返回false
```javascript
m.delete("AAA")		// true
m.delete("DDD")		// false
```

------------


**Map.prototype.clear()**
清空所有元素
```javascript
m.clear()
```


------------



**Map.prototype.forEach()**
遍历元素
```javascript
m.forEach((key, value) => {
	console.log(key)
	console.log(value)
})
```




------------



**Map转数组：**
```javascript
var m = new Map();
m.set('AAA', 18);
m.set('BBB', 19);
m.set('CCC', 20);

[...m.keys()]   // ["AAA", "BBB", "CCC"]
[...m.values()] // [18, 19, 20]
[...m.entries()]    // [["AAA", 18], ["BBB", 19], ["CCC", 20]]
[...m]          // [["AAA", 18], ["BBB", 19], ["CCC", 20]]
```


------------


**Map.groupBy()**
```javascript
let list = [{ name: "Andy", age: 24 }, { name: "Bruce", age: 21 }, { name: "Curry", age: 16 }]

const adult = { check: true }
const child = { check: false }
const result = Map.groupBy(list, (item) => {
	return item.age > 18 ? adult : child
})

console.log(result.get(adult))  // [{ name: "Andy", age: 24 }, { name: "Bruce", age: 21 }]
```