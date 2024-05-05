ES6 也引入了类关键字
```javascript
class Person {
	constructor(name) {
		this.name = name
	}
	speak() {
		console.log("speak")
	}
}

let p1 = new Person("Andy")

// 类的属性和方法都会在其实例上找到（除了类自己静态的）
console.log(p1.name)    // Andy
p1.speak()              // speak
```

------------


所有实例共享同一个原型对象：
```javascript
p1.__proto__ == p2.__proto__ == Person.prototype
```
所以可以通过实例给原型添加属性，进而给其它实例添加属性：
```javascript
let p1 = new Person("Andy")
p1.__proto__.address = "XMU"

let p2 = new Person("Curry")
console.log(p2.address)     // XMU
```

------------


静态变量只能用类名来获得，不能通过实例来获得，并且this指向的是类
```javascript
class Person {
	constructor(name) {
		this.name = name
	}
	speak() {
		console.log("speak")
	}
	static count = 0
	static fn() {
		console.log(this.count)
	}
}

console.log(Person.count)   // 0
Person.count++
Person.fn()                 // 1
```

------------

类的继承，如果使用了继承，子类的构造函数中必须调用 super 方法，否则报错
所以新建子类实例时，父类的构造函数必定会先运行一次
```javascript
class Animal {
	constructor() {
		console.log("我是父类构造方法")
	}
}
class Person extends Animal {
	constructor(name) {
		super()
		console.log("我是子类构造方法")

		this.name = name
	}
}

let p1 = new Person("Andy")     // 我是父类构造方法 我是子类构造方法
```

如果子类没有显式定义构造函数，super 会默认添加，并且会自动调用
```javascript
class Animal {
	constructor() {
		console.log("我是父类构造方法")
	}
}
class Person extends Animal {

}

let p1 = new Person()     // 我是父类构造方法
```

父类的静态属性也会继承
```javascript
class Animal {
	constructor() {

	}
	static num = 0
}
class Person extends Animal {

}

let p1 = new Person()
console.log(Person.num)     // 0
```

```javascript
class Animal {
	constructor() {

	}
	static count = 1
}
class Person extends Animal {
	static count = 2
}

let p1 = new Person()
console.log(Person.count)   // 2
```
