### 模板字符串

```javascript
let message = `Hello World`
console.log(message)   // Hello World
```

```javascript
// 如果恰巧要使用反撇号, 要用反斜杠转义：
let message = `Hello \` World`
console.log(message)   // Hello ` World
```

```javascript
// 在模板字符串中，空格 制表 换行 都会被保留：
let message = `
<ul>
    <li>    </li>
</ul>
`;
console.log(message)
```


```javascript
let str1='Andy'
let str2='21'
console.log(`I'm ${str1} ${str2} years old`)	//I'm Andy 21 years old
```

------------


### 字符串分割：split（）


```javascript
let str = "Andy"
let newstr = str.split("")
console.log(newstr)        //["A", "n", "d", "y"]
```

```javascript
// 利用拓展运算符
let str = 'hello'
let arr = [...str]
console.log(arr)        //["h", "e", "l", "l", "o"]
```

```javascript
let str = "A.n.d.y.."
let newstr = str.split(".")
console.log(newstr)        //["A", "n", "d", "y", "", ""]
```

------------


### 字符串截取 substring（）

```javascript
// 从下标3开始截取，返回一个新字符串：

let str = "abcdefg"
let newstr = str.substring(3)
console.log(str)        //abcdefg
console.log(newstr)        //defg
```

```javascript
// 从3到5，左闭右开 [3，5)

let str = "abcdefg"
let newstr = str.substring(3, 5)
console.log(str)        //abcdefg
console.log(newstr)        //de
```

------------


### 字符串去除空格 trim（）

```javascript
// trim 同时清除左右空格：
let str = ' T esting '
let newstr = str.trim()
console.log(newstr)		//'T esting'
```

```javascript
//trimStart 清除左空格：
let str = ' T esting '
let newstr = str.trimStart()
console.log(newstr)		//'T esting '
```

```javascript
// trimEnd 清除右空格：
let str = ' T esting '
let newstr = str.trimEnd()
console.log(newstr)		//' T esting'
```

```javascript
// 清除字符串所有空格：
let str = ' T esting '
let newstr = str.replaceAll(" ", "")
console.log(newstr)		//'Testing'
```

------------


### 字符串替换 replaceAll（）

```javascript
// 返回一个全新的字符串，所有符合匹配规则的字符都将被替换掉：

const str = '2-4-6-8-10'
const newStr = str.replaceAll('-', '+')
console.log(newStr)        //2+4+6+8+10

const str = 'hello';
const newStr = str.replaceAll('l', ' ');
console.log(newStr);        //he  o

const str = 'hello';
const newStr = str.replaceAll('l', '');
console.log(newStr);        //heo

let str = ' T esting '
let newstr = str.replaceAll(" ", "");
console.log(newstr)        //Testing
```

------------


### 字符串填充 padEnd（）

```javascript
const str = 'hello'
const newStr = str.padStart(10,6)
console.log(newStr)		//66666hello
```

```javascript
const str = 'hello';
const newStr = str.padEnd(10,6);
console.log(newStr);		//hello66666
```

------------


### 字符串转大小写

```javascript
// 大写：
let str = "Andy";
let newstr = str.toUpperCase();
```

```javascript
// 小写：
let str = "Andy";
let newstr = str.toLowerCase();
```

------------

### startsWith（） 和 endsWith（）
```javascript
let str = "hello,es6!"
console.log(str.startsWith("hello"))	// true
console.log(str.startsWith(""))		// true
console.log(str.endsWith("es6!"))	// true
```

------------

### 数字字符
```javascript
// 通过_下划线来分割数字，使数字化可计算：

const money = 1_234_567
console.log(money === 1234567)	//true
console.log(money)    		//123467
```

```javascript
// 当数字是四位及以上时，toLocaleString()会让数字三位三位一分隔：

let num = 1111111
console.log(num.toString())		//1111111
console.log(num.toLocaleString())		//1,111,111
```

```javascript
// 转换时间格式上有区别：

let date = new Date()
console.log(date.toString())		//Fri Mar 11 2022 09:40:38 GMT+0800 (中国标准时间)
console.log(date.toLocaleString())	//2022/3/11 上午9:40:38
```
