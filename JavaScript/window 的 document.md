
---

**直接访问 DOM 节点的方法：**

- **document.getElementById("andy")，通过id获取**
```javascript
// id是唯一的，不能重复，所以只能获取到一个节点
console.log(document.getElementById("andy").innerText)
```

- **document.getElementsByTagName("p")，通过标签获取**
```javascript
// 获取的是一个list，需指定第几个元素
console.log(document.getElementsByTagName("p")[0].innerText)
console.log(document.getElementsByTagName("p")[1].innerText)
```

- **document.getElementsByClassName("class-andy")，通过类名获取**
```javascript
// 获取的是一个list，需指定第几个元素
console.log(document.getElementsByClassName("class-andy")[0].innerText)
console.log(document.getElementsByClassName("class-andy")[1].innerText)
```

- **document.querySelector("li")**
```javascript
// 匹配第一个元素
console.log(document.querySelector('li').innerText)
```

- **document.querySelectorAll("li")**
```javascript
// 获取的是一个list，需指定第几个元素
console.log(document.querySelectorAll('li')[0].innerText)
console.log(document.querySelectorAll('li')[1].innerText)
```

------------

**间接访问 DOM 节点的方法：**

- **通过父节点访问子节点**
```javascript
// 第一个子节点
console.log(document.getElementById("andy").querySelector("p:first-child").innerHTML)
// 最后一个子节点
console.log(document.getElementById("andy").querySelector("p:last-child").innerHTML)
```

- **通过子节点访问父节点再访问其他子节点**
```javascript
console.log(document.getElementById("p1").parentNode.querySelector("p:last-child").innerHTML)
```

------------

**DOM 节点属性的修改**

- 修改文本
```javascript
// innerText 不可以解析标签
document.getElementById("andy").innerText = "<strong>Andy</strong>"
// innerHTML 可以解析标签
document.getElementById("andy").innerHTML = "<strong>Andy</strong>"
```

- 修改样式
```javascript
document.getElementById("andy").style.color="red"
```

- 修改 class
```javascript
// className 可以覆盖之前的样式
document.getElementById("andy").className = 'cs1 cs2'
```

```javascript
// classList 可以追加和删除样式，不影响之前的样式
document.getElementById("andy").classList.add('cs1')        // 添加
document.getElementById("andy").classList.remove('cs1')     // 删除
document.getElementById("andy").classList.toggle('cs1')     // 切换	应用在开关上
```

------------

**DOM 节点的增加**

- appendChild(node)，添加子节点 node（至最后）
```html
<div id="andy">
	<p>aaa</p>
	<p>bbb</p>
</div>
```

```javascript
const node = document.createElement("p")
// 将节点 p 添加到 id 为 andy 的节点下面
document.getElementById("andy").appendChild(node)
// 之后可以对 p 节点的属性进行设置
node.innerText = "ccc"
```

```html
// 结果
<div id="andy">
	<p>aaa</p>
	<p>bbb</p>
	<p>ccc</p>
</div>
```

- insertBefore(node，b1)，添加子节点node（至b1节点前）
```html
<div id="andy">
	<p>aaa</p>
	<p>bbb</p>
</div>
```
```javascript
// 新建一个节点 p
const node = document.createElement("p")
// 获取 id 为 b1 的节点
const b1 = document.getElementById("b1")
// 将节点 p 添加到 id 为 b1 的节点之前
document.getElementById("andy").insertBefore(node, b1)
// 之后可以对 p 节点的属性进行设置
node.innerText = "ccc"
```
```html
// 结果
<div id="andy">
	<p>aaa</p>
	<p>ccc</p>
	<p>bbb</p>
</div>
```

------------

**DOM 节点的删除**

- removeChild(b1)，删除子节点 b1
```html
<div id="andy">
	<p>aaa</p>
	<p>bbb</p>
</div>
```
```javascript
// 获取 id 为 b1 的节点
const b1 = document.getElementById("b1")
// 删除 id 为 andy 下的 b1 节点
document.getElementById("andy").removeChild(b1)
```
```html
// 结果
<div id="andy">
	<p>aaa</p>
</div>
```

**有个好方法，可以不用知道具体的父元素，可以使用 parentNode 属性来查找其父元素：**
```javascript
document.getElementById("b1").parentNode.removeChild(b1)
```


