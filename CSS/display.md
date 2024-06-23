
---

**display : inline**
可以将块元素放在一行，不能设置宽高，但可以设置内外边距（此时两个元素中间有空隙）

```css
<div class="andy">Andy</div>
<div class="andy">Andy</div>
		
.andy {
	width: 100px;
	height: 50px;
	background-color: red;
	margin: 10px;
	display: inline;
}
```

![[Pasted image 20240623205248.png]]

------------

**display : block**
可以将行内元素变成块元素，可以设置宽高，可以独占一行

```css
.andy {
	width: 100px;
	height: 50px;
	background-color: red;
	display: block;
}
```

![[Pasted image 20240623205301.png]]

------------

**display : inline-block**
可以将 块元素 放在同一行（此时两个元素中间有空隙）

```css
<div class="andy">Andy</div>
<div class="andy">Andy</div>
		
.andy {
	width: 100px;
	height: 50px;
	background-color: red;
	display: inline-block;
}
```

![[Pasted image 20240623205322.png]]

------------

**问题：为什么两个元素中间有空隙？**

元素被当成行内元素排版的时候，元素之间的空白符（空格、回车换行等）都会被浏览器处理

- 解法一：将html这样写，空隙会消除：
```css
<div class="andy">Andy</div><div class="andy">Andy</div>
```

- 解法二：在父元素添加：
```css
{
	word-spacing: -1em;
}
```