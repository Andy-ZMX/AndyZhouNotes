
---

别忘了加 break

```javascript
switch (3) {
	case 1:
		console.log('1')
		break
		case 2:
		console.log('2')
		break
		case 3:
		console.log('3')	// 3
		break
		default:
		console.log('0')
}
```

------------

如果没加 break，即使下一个 case 不符合，也会进入

```javascript
switch (3) {
	case 1:
		console.log('1')
		break
		case 2:
		console.log('2')
		break
		case 3:
		console.log('3')	// 3
		default:
		console.log('0')	// 0
}
```