
---

**arguments 可以动态获取函数的实参，是伪数组**

```javascript
function fn() {
	console.log(arguments[0])       // a
	console.log(arguments.length)   // 3
}
fn("a", "b", "c")
```

------------

**用 ... 是真数组**

```javascript
function fn(a, ...b) {
	console.log(a)      // a
	console.log(b)      // ['b', 'c']
}
fn("a", "b", "c")
```