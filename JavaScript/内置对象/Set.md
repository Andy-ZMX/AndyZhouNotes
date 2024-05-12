#### Set 可以存储任何类型的值，有相同的值会去重

------------

**Set.prototype.add()**
添加元素，如果已存在，则不进行任何操作
```javascript
const result = new Set()
result.add(1)
result.add(2)
result.add(3)
result.add(1)		// 跟前面的数据重复
console.log(result)		// Set(3) {1, 2, 3}
```
Set的参数不一定是数组，只要是可迭代对象都可以
```javascript
const result = new Set([1,3,3,4,5,5,6])
console.log(result)		// Set(5) {1, 3, 4, 5, 6}

const result = new Set('abbccdde')
console.log(result)		// Set(5) {'a', 'b', 'c', 'd', 'e'}
```

------------

**Set.prototype.delete()**
删除匹配的数据，返回是否删除成功
```javascript
const result = new Set()
result.add(1)
result.delete(1)		// true
result.delete(3)		// false
```

------------

**Set.prototype.has()**
判断Set中是否存在对应的数据
```javascript
const result = new Set()
result.add(1)
result.add(2)
result.has(1)		// true
result.has(3)		// false
```

------------

**Set.prototype.clear()**
清空
```javascript
result.clear()
```

------------

**Set.prototype.forEach()**
遍历
```javascript
const result = new Set()
result.add(1)
result.add(2)
result.add(3)

result.forEach((item) => {
	console.log(item)   // 1, 2, 3
})
```

------------

**字符串去重**
```javascript
var str = 'aabbbcccd';
const result = [...new Set(str)].join("");

console.log(result);		// abcd
```

------------

**数组去重**
```javascript
const arr = [1, 2, 3, 1, 2, 4];
const newarr = [...new Set(arr)];

console.log(newarr)		// [1,2,3,4]
```

```javascript
const arr = [1, 2, 3, 1, 2, 4];
const newarr = Array.from(new Set(arr));

console.log(newarr)        // [1,2,3,4]
```

------------

**并集**
```javascript
const set1 = new Set([1,2,3])
const set2 = new Set([2,3,4])
const union = new Set([...set1,...set2])	// {1, 2, 3, 4}
```

------------

**交集**
```javascript
const set1 = new Set([1,2,3])
const set2 = new Set([2,3,4])
const intersection = new Set([...set1].filter(item => set2.has(item)))	// {2, 3}
```
