
---
#### Object.assign()

可以将对象合并至目标对象，同名属性会被覆盖，返回合并后的目标对象

```javascript
const target = { a: 1, b: 2 }
const source1 = { b: 4, c: 5 }
const source2 = { b: 5, d: 6 };

const returnedTarget = Object.assign(target, source1, source2)

console.log(returnedTarget)     // {a: 1, b: 5, c: 5, d: 6}
console.log(returnedTarget === target)  // true
```

拷贝问题：

```javascript
const obj1 = { a: 0, b: { c: 0 } }
const obj2 = Object.assign({}, obj1)

// 正常拷贝
obj1.a = 1
console.log(obj1)   // { a: 1, b: { c: 0 } }
console.log(obj2)   // { a: 0, b: { c: 0 } }

// 浅拷贝
obj2.b.c = 3
console.log(obj1)   // { a: 1, b: { c: 3 } }
console.log(obj2)   // { a: 1, b: { c: 3 } }

// 深拷贝
const obj3 = { a: 0, b: { c: 0 } }
const obj4 = JSON.parse(JSON.stringify(obj3))
obj3.a = 4
obj3.b.c = 4
console.log(obj4)	// { a: 0, b: { c: 0 } }
```

------------
#### Object.defineProperty()

可以直接在一个对象上定义一个新属性，或修改其现有属性，并返回此对象

```javascript
const obj = { name: "Andy" }

Object.defineProperty(obj, 'name', {
	value: "Curry"
})

Object.defineProperty(obj, 'age', {
	value: "24",
	writable: false
})

console.log(obj)    // {name: 'Curry', age: '24'}
```

定义的属性默认是不可枚举的（用in遍历不到）

------------
#### Object.keys() 和 Object.values() 和 Object.entries() 和 Object.fromEntries()

```javascript
const obj = { name: "Andy", age: "24", address: "XMU" }

console.log(Object.keys(obj))       // ['name', 'age', 'address']
console.log(Object.values(obj))     // ['Andy', '24', 'XMU']
console.log(Object.entries(obj))    // [['name', 'Andy'], ['age', '24'], ['address', 'XMU']]
console.log(Object.fromEntries(Object.entries(obj)))  // { name: "Andy", age: "24", address: "XMU" }
```

------------
#### Object.freeze()

使一个对象被冻结，被冻结的对象不能再被更改，返回与传入的对象相同的对象（浅冻结）

```javascript
const obj = { name: "Andy", age: "24", address: "XMU" }
Object.freeze(obj)

obj.name = "Curry"
console.log(obj)    // {name: 'Andy', age: '24', address: 'XMU'}

console.log(Object.isFrozen(obj))   // true
```

------------
#### Object.seal()

不同于 Object.freeze() 的是，通过 Object.seal() 密封的对象可以更改其现有属性，只要它们是可写的
同样也有个：**Object.isSealed()**

------------

#### Object.getOwnPropertyNames()

返回对象的属性值（包括不可枚举的属性）

```javascript
const obj = { name: "Andy", age: "24", address: "XMU" }

Object.defineProperty(obj, "aaa", {
	value: "lalala"
})

console.log(Object.keys(obj))   // ['name', 'age', 'address']
console.log(Object.getOwnPropertyNames(obj))    // ['name', 'age', 'address', 'aaa']
```

------------
#### Object.getPrototypeOf()

获取对象的原型

```javascript
const obj = { name: "Andy", age: "24", address: "XMU" }

Object.getPrototypeOf(obj) === obj.__proto__	// true
```

------------
#### Object.hasOwn()

查询对象是否有某个属性（继承的或者不存在，该方法返回 false）

```javascript
const obj = { name: "Andy", age: "24", address: "XMU" }

console.log(Object.hasOwn(obj, "name"))     // true
console.log(Object.hasOwn(obj, "aaa"))      // false
```

此方法用于替代 Object.prototype.hasOwnProperty()

```javascript
const foo = Object.create(null)
foo.prop = "exists"

console.log(Object.hasOwn(foo, "prop"))     // true  无论对象是如何创建的，它都可以运行
console.log(foo.hasOwnProperty("name"))     // 报错
```