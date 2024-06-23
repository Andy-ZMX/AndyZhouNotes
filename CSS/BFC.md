
---

**BFC(Block Formatting Context) 块级格式化上下文**
是页面上一块独立的渲染区域，内部元素盒子都按照其特定的规则进行排列渲染，且区域内的布局与区域外的布局不相互影响。

------------

**如何触发BFC：**
- display: flex;
- overflow: auto;

------------

**可以避免margin重叠：**

```css
<div class="aaa">aaa</div>
<div class="bbb">bbb</div>

.aaa {
	width: 200px;
	height: 100px;
	background-color: red;
	margin-bottom: 10px;
}
.bbb {
	width: 200px;
	height: 100px;
	background-color: green;
	margin-top: 20px;
}
```

按理来说两个 div 之间的 margin 应该是 10+20=30px，但是实际效果是两个数只取较大的值来算
所以可以使用 BFC 来解决，将其中一个 div 用 BFC 包裹起来：

```css
<div class="aaa">aaa</div>
<div class="bfc">
	<div class="bbb">bbb</div>
</div>

.aaa {
	width: 200px;
	height: 100px;
	background-color: red;
	margin-bottom: 10px;
}
.bbb {
	width: 200px;
	height: 100px;
	background-color: green;
	margin-top: 20px;
}
.bfc {
	overflow: auto;
}
```

不用包裹也可以，两个 div 中间夹一个也行：

```css
<div class="aaa">aaa</div>
<div class="bfc"></div>
<div class="bbb">bbb</div>

.aaa {
	width: 200px;
	height: 100px;
	background-color: red;
	margin-bottom: 10px;
}
.bbb {
	width: 200px;
	height: 100px;
	background-color: green;
	margin-top: 20px;
}
.bfc {
	overflow: auto;
}
```

------------

**可以避免margin塌陷：**
```css
<div class="aaa">
	<div class="bbb">bbb</div>
</div>

.aaa {
	width: 200px;
	height: 100px;
	background-color: red;
}
.bbb {
	width: 100px;
	height: 50px;
	background-color: green;
	margin-top: 20px;
}
```

按理来说子元素顶部距离父元素顶部为 20px，但是实际上子元素顶部紧贴父元素顶部，而父元素顶部距离其它元素为 20px，看上去就像子元素带着父元素一起掉了下来：

![[Pasted image 20240623221440.png]]

所以可以使用 BFC 来解决，将子元素用 BFC 包裹起来：

```css
<div class="aaa">
	<div class="bfc">
		<div class="bbb">bbb</div>
	</div>
</div>

.aaa {
	width: 200px;
	height: 100px;
	background-color: red;
}
.bbb {
	width: 100px;
	height: 50px;
	background-color: green;
	margin-top: 20px;
}
```

同样不用包裹也可以，子元素上边再放一个 BFC 也行：

```css
<div class="aaa">
	<div class="bfc"></div>
	<div class="bbb">bbb</div>
</div>

.aaa {
	width: 200px;
	height: 100px;
	background-color: red;
}
.bbb {
	width: 100px;
	height: 50px;
	background-color: green;
	margin-top: 20px;
}
```

------------

https://blog.csdn.net/qq_35727582/article/details/116156095?spm=1001.2014.3001.5506