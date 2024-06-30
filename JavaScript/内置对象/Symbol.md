
---
#### 应用1：消除魔术字符串

字符串 Triangle 和 Rectangle 都是魔术字符串，它们多次出现，与代码形成“强耦合”，不利于将来的修改和维护：

```javascript
function getArea(shape, width, height) {
	let area = 0
	switch (shape) {
		case 'Triangle':
			area = width * height * 0.5
			break
		case 'Rectangle':
			area = width * height
			break
	}
	console.log(area)
}

getArea('Triangle', 10, 20)
```

常用的消除魔术字符串的方法，就是把它写成一个变量：

```javascript
const shapeType = {
	triangle: 'Triangle',
	rectangle: 'Rectangle'
}

function getArea(shape, width, height) {
	let area = 0
	switch (shape) {
		case shapeType.triangle:
			area = width * height * 0.5
			break
		case shapeType.triangle:
			area = width * height
			break
	}
	console.log(area)
}

getArea(shapeType.triangle, 10, 20)
```


如果仔细分析，可以发现shapeType.triangle等于哪个值并不重要，只要确保不会跟其他shapeType属性的值冲突即可
因此，这里就很适合改用 Symbol 值：

```javascript
const shapeType = {
	triangle: Symbol(),
	rectangle: Symbol()
}

function getArea(shape, width, height) {
	let area = 0
	switch (shape) {
		case shapeType.triangle:
			area = width * height * 0.5
			break
		case shapeType.triangle:
			area = width * height
			break
	}
	console.log(area)
}

getArea(shapeType.triangle, 10, 20)
```

------------
#### 应用2：避免属性污染

```javascript
let address = Symbol("address")

let person = {
  name: "Andy",
  age: 24,
  address: "XiaMen"
}

person[address] = "Xian"
console.log(person)   // {name: 'Andy', age: 24, address: 'XiaMen', Symbol(address): 'Xian'}
```

```javascript
let address = Symbol("address")

let person = {
  name: "Andy",
  age: 24,
  address: "XiaMen",
  [address]: "Xian"
}

console.log(person)   // {name: 'Andy', age: 24, address: 'XiaMen', Symbol(address): 'Xian'}
```

- Symbol 作为对象属性名时读取时不能用.运算符，要用方括号
- for...in 、 for...of 的循环中不会出现该属性，Object.keys() 和 Object.getOwnPropertyNames() 也不会
- 可以通过 Object.getOwnPropertySymbols() 和 Reflect.ownKeys() 取到

------------

#### 应用3：模块内部状态封装

使用 Symbol 创建一个私有的 key，外部代码无法直接访问 _age，只能通过暴露的方法来间接访问

```javascript
let _age = Symbol("age")

let person = {
    name: "Andy",
    [_age]: 24,
    addAge() {
        this[_age]++
    },
    getAge() {
        return this[_age]
    }
}

export default person
```
```javascript
import person from './person.js'
	
person.addAge()
console.log(person.getAge())
```

------------

https://juejin.cn/post/6918014088967061511