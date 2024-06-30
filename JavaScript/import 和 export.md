
---

**export：可以导出多个**

```javascript
// 先导出后定义
export { name, sayHello }

let name = "Andy"
function sayHello() {
    console.log("Hello")
}
```

```javascript
// 先定义后导出
let name = "Andy"
function sayHello() {
    console.log("Hello")
}

export { name, sayHello }
```

```javascript
// 挨个导出
export let name = "Andy"
export function sayHello() {
    console.log("Hello")
}
```

------------

**export default：只能导出一个**

```javascript
// 先定义后导出
function sayHello() {
    console.log("Hello")
}
export default sayHello
```

```javascript
// 直接导出
export default function sayHello() {
    console.log("Hello")
}
```

------------

**export 的 import：**

```javascript
// 普通 import
import { name, sayHello } from './test.js'
console.log(name)
sayHello()
```

```javascript
// 可以重命名
import { name as a, sayHello as b } from './test.js'
console.log(a)
b()
```

```javascript
// 可以用 *
import * as test from './test.js'
console.log(test.name)
test.sayHello()
```

------------

**export default 的 import：**

```javascript
// 普通 import，不用加大括号
import sayHello from "./test.js"
sayHello()
```

```javascript
// 重命名，由于export default默认导出一个，所以可以不用as重命名
import fn from "./test.js"
fn()
```

------------

**有点像hooks**

```javascript
export const useAndy = function () {
    let name = 'Andy'
    let fn = function () {
        console.log('fn')
    }
    return { name, fn }
}
```
```javascript
import { useAndy } from '@/hooks'	// 如果是index可以省略文件名

const andy = useAndy()
console.log(andy.name)  // Andy
andy.fn()   // fn
```

---

**动态 import**

```javascript
import('./test.js').then((data) => {
  console.log(data.name)
})
```

---

**普通 html 使用外部 JS**

```javascript
// 普通html
<head>
    <script type="text/javascript" src="./test.js"></script>
</head>
<body>
    <script>
        console.log(person)
    </script>
</body>
```

```javascript
// test.js:
var person = "Andy";
```