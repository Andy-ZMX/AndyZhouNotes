
```javascript
let obj = {
	name: 'Andy',
	age: '24',
	address: 'XMU'
}

let result_1 = JSON.stringify(obj)
console.log(result_1)        // {"name":"Andy","age":"24","address":"XMU"}

let result_2 = JSON.stringify(obj, ['name'])
console.log(result_2)       // {"name":"Andy"}

let result_3 = JSON.parse(result_1)     // 可以再将 string 转为 object
```