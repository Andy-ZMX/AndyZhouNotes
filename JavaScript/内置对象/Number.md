### 四舍五入取整
```javascript
console.log(Math.ceil(1.2))     // 2 向上取整
console.log(Math.ceil(-1.2))    // -1 向上取整

console.log(Math.floor(1.2))    // 1 向下取整
console.log(Math.floor(-1.2))   // -2 向下取整

console.log(Math.round(1.2))    // 1 四舍五入
console.log(Math.round(1.5))    // 2 四舍五入
console.log(Math.round(-1.2))   // -1 四舍五入
console.log(Math.round(-1.5))   // -1 四舍五入  特殊
console.log(Math.round(-1.6))   // -2 四舍五入
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

------------

### 随机数
```javascript
Math.random()				// 返回一个小数 [0,1)
Math.random() * (10 + 1)	// 返回一个小数 [0,11)
Math.floor(Math.random() * 11)	// 返回一个 0 到 10 的整数 [0,10]
parseInt(Math.random() * (max - min + 1) + min , 10)	// 获取 min ~ max 的整数
```