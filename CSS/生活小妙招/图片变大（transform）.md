
---

**图片在规定范围内变大**

```html
<div class="a">
	<img src="./Andy.jpg" />
</div>
```

```css
<style>
    .a {
        width: 1200px;
        height: 320px;
        overflow: hidden;
    }

    img {
        transition: all 0.8s;
    }

    img:hover {
        transform: scale(1.2);
    }
</style>
```

---

**图片变大**

```html
<div class="tran"></div>
```

```css
<style>
    .tran {
        width: 100px;
        height: 100px;
        background: red;
        transition: height 2s, width 2s;
    }

    .tran:hover {
        width: 300px;
        height: 300px;
    }
</style>
```