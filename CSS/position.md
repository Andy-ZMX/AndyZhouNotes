
---

**absolute：脱离文本流**

```css
<style>
    .one {
        width: 300px;
        height: 50px;
        background-color: red;
    }

    .two {
        width: 300px;
        height: 50px;
        background-color: green;
        position: absolute;
        top: 30px;
        left: 30px;
    }

    .three {
        width: 300px;
        height: 50px;
        background-color: blue;
    }
</style>
```
![[Pasted image 20240623144011.png]]

------------

**relative**
```css
<style>
    .one {
        width: 300px;
        height: 50px;
        background-color: red;
    }

    .two {
        width: 300px;
        height: 50px;
        background-color: green;
        position: relative;
        top: 30px;
        left: 30px;
    }

    .three {
        width: 300px;
        height: 50px;
        background-color: blue;
    }
</style>
```
![[Pasted image 20240623144022.png]]

------------

**fixed：**
脱离文档流，元素的位置相对于浏览器窗口是固定位置，即使窗口是滚动的它也不会移动

------------

**sticky：**
正常看没啥特殊的，但随着滚动条滚出目标区域后，它会定在某一位置（top, left, right, bottom 必须得设置值）

------------

**z-index**
越大越在上层