
---

**窗口加载事件：**

window.onload是页面加载事件，完全加载（DOM，图像，CSS）之后会执行

```javascript
    <script>
        window.onload = function () {
            let btn = document.querySelector('button');
            btn.addEventListener('click', function () {
                alert('点击了');
            })
        }
    </script>
```

------------

window.onload只能写一次，如果有多个，只会执行最后一个
有个新方法可以写多个onload：

```javascript
    <script>
        window.addEventListener('load', function () {
            let btn = document.querySelector('button');
            btn.addEventListener('click', function () {
                alert('点击了');
            })
        })

        window.addEventListener('load', function () {
            alert('加载了');
        })
    </script>
```

------------

有一个先于onload的事件：DOMContentLoaded
仅当加载（DOM）之后会执行，不包括：图像，CSS
会先 DOMContentLoaded 再 load，适用于有很多图片的页面

```javascript
    <script>
        window.addEventListener('load', function () {
            alert('load');
        })

        window.addEventListener('DOMContentLoaded', function () {
            alert('DOMContentLoaded');
        })
    </script>
```

