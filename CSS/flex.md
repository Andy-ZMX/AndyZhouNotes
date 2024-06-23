
---

**justify-content: space-between**

表示在 flex 容器中，所有元素均等分剩余比例，并且两边顶格
![[Pasted image 20240623143511.png]]

------------

**justify-content: space-around**

表示在 flex 容器中，所有元素均等分剩余比例，并且两边不顶格
![[Pasted image 20240623143523.png]]

------------

**flex-grow: 1**

表示在 flex 容器中，元素所占剩余空间的比例

```html
<body>
    <div class="andy">
        <div class="child-one"></div>
        <div class="child-two"></div>
    </div>
</body>

<style>
    .andy {
        display: flex;
    }

    .child-one{
        height: 50px;
        background-color: red;
        flex-grow: 1;
    }

    .child-two {
        height: 50px;
        background-color: aqua;
        flex-grow: 2;
    }
</style>
```

![[Pasted image 20240623143548.png]]

------------

**最后一个元素右对齐**

内容按顺序从左到右排列，但是最后一个元素右对齐，这时上面的布局就不适用了
可以设置最后一个子元素：margin-left: auto;

```css
.child-two {
  width: 100px;
  height: 50px;
  background-color: aqua;
  margin-left: auto;
}
```