
---

**addEventListener 事件：**

```javascript
const div = document.querySelector('div')

div.addEventListener('click', (e) => {
  console.log(e.type)     // 事件类型
  console.log(e.clientX)  // 相对于浏览器窗口左上角的坐标
  console.log(e.clientY)
  console.log(e.offsetX)  // 相对于DOM元素左上角的坐标
  console.log(e.offsetY)
})
```

------------

**常见的事件：**

- 鼠标进入：mouseenter
- 鼠标移出：mouseleave
- 获得焦点：focus
- 失去焦点：blur
- 键盘按下：keydown
- 键盘弹起：keyup

------------

**addEventListener 也有第三个参数，默认是 false，使用冒泡**

```html
<div id="red">
	<div id="green">
		<div id="blue">Andy</div>
	</div>
</div>
```
```javascript
document.getElementById("red").addEventListener('click', (e) => {
	console.log('冒泡red')
})
document.getElementById("green").addEventListener('click', (e) => {
	console.log('冒泡green')
})
document.getElementById("blue").addEventListener('click', (e) => {
	console.log('冒泡blue')
})

// 输出 冒泡blue 冒泡green 冒泡red
```

------------

**addEventListener 的第三个参数，如果是 true，使用捕获**

```html
<div id="red">
	<div id="green">
		<div id="blue">Andy</div>
	</div>
</div>
```
```javascript
document.getElementById("red").addEventListener('click', (e) => {
	console.log('捕获red')
}, true)
document.getElementById("green").addEventListener('click', (e) => {
	console.log('捕获green')
}, true)
document.getElementById("blue").addEventListener('click', (e) => {
	console.log('捕获blue')
}, true)

// 输出 捕获red 捕获green 捕获blue
```

------------

**如果同时存在就是 先捕获后冒泡：**

```javascript
document.getElementById("red").addEventListener('click', (e) => {
	console.log('冒泡red')
})
document.getElementById("green").addEventListener('click', (e) => {
	console.log('冒泡green')
})
document.getElementById("blue").addEventListener('click', (e) => {
	console.log('冒泡blue')
})
document.getElementById("red").addEventListener('click', (e) => {
	console.log('捕获red')
}, true)
document.getElementById("green").addEventListener('click', (e) => {
	console.log('捕获green')
}, true)
document.getElementById("blue").addEventListener('click', (e) => {
	console.log('捕获blue')
}, true)

// 输出 捕获red 捕获green 捕获blue 冒泡blue 冒泡green 冒泡red
```

------------

**如果想在中间停止捕获冒泡：使用 stopPropagation（）方法：**

```javascript
document.getElementById("red").addEventListener('click', (e) => {
	console.log('冒泡red')
})
document.getElementById("green").addEventListener('click', (e) => {
	console.log('冒泡green')
})
document.getElementById("blue").addEventListener('click', (e) => {
	console.log('冒泡blue')
})
document.getElementById("red").addEventListener('click', (e) => {
	console.log('捕获red')
}, true)
document.getElementById("green").addEventListener('click', (e) => {
	console.log('捕获green')
	e.stopPropagation()
}, true)
document.getElementById("blue").addEventListener('click', (e) => {
	console.log('捕获blue')
}, true)

// 输出 捕获red 捕获green（就停了）
```

------------

**事件委托：给父元素添加事件监听，为了减少注册次数，提高程序性能**

```html
<ul>
	<li>111</li>
	<li>222</li>
	<li>333</li>
	<div>444</div>
</ul>
```
```javascript
document.querySelector("ul").addEventListener('click', (e) => {
	if (e.target.tagName == 'LI') {
		e.target.style.color = 'blue'
	}

	if (e.target.tagName == 'DIV') {
		e.target.style.color = 'red'
	}
})
```