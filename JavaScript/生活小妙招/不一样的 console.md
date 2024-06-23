
**显示功能：**

```javascript
console.log("这是log");
console.warn("这是warn");
console.error("这是error");
```
![[Pasted image 20240623140229.png]]

------------

**计时功能：**

```javascript
console.time('execute time');

for (let i = 0; i < 1000; i++) {
  for (let j = 0; j < 1000; j++) { }
}

console.timeEnd('execute time');
```
![[Pasted image 20240623140244.png]]

------------

**分组功能：**

```javascript
console.group("第一组信息");
console.log("第一组第一条");
console.log("第一组第二条");
console.groupEnd();

console.group("第二组信息");
console.log("第二组第一条");
console.log("第二组第二条");
console.groupEnd();
```
![[Pasted image 20240623140308.png]]

------------

**占位符：**

```javascript
console.log("%d年%d月%d日", 2022, 11, 1);
console.log("圆周率是%f", 3.1415926);
```
![[Pasted image 20240623140317.png]]

```javascript
console.log('123%c456', 'color: red;')
console.log('%c123%c456', 'color: pink;', 'color: red;')
```
![[Pasted image 20240623140338.png]]

------------

**使用chalk：**

```javascript
// npm i @alita/chalk

import chalk from '@alita/chalk';
window.alitadebug = true;
chalk.hello('Version', '5.2.0');
```
![[Pasted image 20240623140353.png]]
