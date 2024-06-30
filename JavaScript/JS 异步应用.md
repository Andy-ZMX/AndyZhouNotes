
---

什么是同步和异步，以通信举例：

在同步通信中，发送方在发出数据后，会等待接收方发回响应，然后才发下一个数据包。也就是说，发送方会一直等待，直到收到返回信息才继续执行下去。
在异步通信中，发送方发出数据后，不等接收方发回响应，就接着发送下一个数据包。这样，发送方不需要一直等待下去，而是可以继续执行下面的操作。当有信息返回时，异步操作会通知进程进行处理。这样可以提高执行的效率。

------------

js中实现异步的方法，就是回调函数：

```javascript
setTimeout(() => {
	console.log("a")
}, 1000)

setTimeout(() => {
	console.log("b")
}, 1000)

setTimeout(() => {
	console.log("c")
}, 1000)
```

程序不用先等1s打印出a，再等1s打印出b，再等1s打印出c，一共用时3s
而是，在1s之后几乎同时打印出 a、b、c，一共用时1s

------------

现在有个新场景，还是通信的例子，发送方需要每次携带上一次接收方回传的信息，这时就需要异步操作的嵌套了（好像是将异步变回同步了）：

```javascript
setTimeout(() => {
	console.log("a")
	setTimeout(() => {
		console.log("b")
		setTimeout(() => {
			console.log("c")
		}, 1000)
	}, 1000)
}, 1000)
```

程序先等1s打印出a，再等1s打印出b，再等1s打印出c，一共用时3s
这样写回调嵌套也不是不行，但如果嵌套的过多，代码不是纵向发展，而是横向发展了，这种现象就叫 回调函数地狱（callback hell）

------------

于是有了新的写法：Promise 对象
它是回调函数地狱的改善方法

```javascript
let promise = new Promise((resolve, reject) => {
	resolve()
}).then(() => {
	return new Promise((resolve) => {
		setTimeout(() => {
			console.log("a")
			resolve()
		}, 1000)
	})
}).then(() => {
	return new Promise((resolve) => {
		setTimeout(() => {
			console.log("b")
			resolve()
		}, 1000)
	})
}).then(() => {
	return new Promise((resolve) => {
		setTimeout(() => {
			console.log("c")
			resolve()
		}, 1000)
	})
})
```

程序同样先等1s打印出a，再等1s打印出b，再等1s打印出c，一共用时3s
Promise 的写法可以将回调的嵌套写法改为链式调用，用一堆 then 连起来
但是还有个问题，原来的写法被 Promise 包装了一下，一眼看去都是一堆then，原来的语义变得很不清楚，代码感觉有点冗余

Promise 对象具体语法：https://www.showdoc.com.cn/2252745344042208/10520450474529485

------------

于是有了新的写法：使用 Generator 函数

```javascript
function* generator() {
	yield new Promise((resolve) => {
		setTimeout(() => {
			console.log("a")
			resolve()
		}, 1000)
	})
	yield new Promise((resolve) => {
		setTimeout(() => {
			console.log("b")
			resolve()
		}, 1000)
	})
	yield new Promise((resolve) => {
		setTimeout(() => {
			console.log("c")
			resolve()
		}, 1000)
	})
}

const gen = generator()
gen.next().value
	.then(() => gen.next().value)
	.then(() => gen.next().value)
```

程序同样先等1s打印出a，再等1s打印出b，再等1s打印出c，一共用时3s

调用 Generator 函数后，该函数并不执行，返回的是一个指向内部状态的指针对象，每次都得调用 next 方法，使得指针移向下一个状态，每次调用next方法，内部指针就从函数头部或上一次停下来的地方开始执行，直到遇到下一个yield表达式（或return语句）为止，换言之，Generator 函数是分段执行的，yield表达式是暂停执行的标记，而next方法可以恢复执行，哎，这几个 next 看起来是真麻烦

Generator 函数具体语法：https://www.showdoc.com.cn/2252745344042208/10627006434882099

------------

有个新函数，async 函数，它就是 Generator 函数的语法糖
上边的代码可以这么写：

```javascript
async function fn() {
	await new Promise((resolve) => {
		setTimeout(() => {
			console.log("a")
			resolve()
		}, 1000)
	})
	await new Promise((resolve) => {
		setTimeout(() => {
			console.log("b")
			resolve()
		}, 1000)
	})
	await new Promise((resolve) => {
		setTimeout(() => {
			console.log("c")
			resolve()
		}, 1000)
	})
}

fn()
```

程序同样先等1s打印出a，再等1s打印出b，再等1s打印出c，一共用时3s
这回看起来好看多了，就像同步代码一样
async 函数具体语法：https://www.showdoc.com.cn/2252745344042208/10515973360767503