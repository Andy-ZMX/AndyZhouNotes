
---

**用js添加css，将一条新的规则插入到样式表的指定位置**

```html
<style>
    /* 第0个style */
</style>

<style>
    /* 第1个style */
    p {
        color: red;
    }
</style>
```

```html
<script>
    console.log(document.styleSheets.length)    // 2    表示一共有两个 style

    console.log(document.styleSheets[1].cssRules.length)    // 1    表示在下标为 1 的 style 中，有 1 个样式

    document.styleSheets[1].insertRule("p {color : green}", document.styleSheets[1].cssRules.length)
</script>
```