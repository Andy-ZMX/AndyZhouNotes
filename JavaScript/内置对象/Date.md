```javascript
function getCurrentDateTime() {
	var currentDate = new Date()

	var year = currentDate.getFullYear()
	var month = ("0" + (currentDate.getMonth() + 1)).slice(-2)
	var day = ("0" + currentDate.getDate()).slice(-2)
	var hours = ("0" + currentDate.getHours()).slice(-2)
	var minutes = ("0" + currentDate.getMinutes()).slice(-2)
	var seconds = ("0" + currentDate.getSeconds()).slice(-2)
	var milliseconds = ("00" + currentDate.getMilliseconds()).slice(-3)

	var formattedDateTime = year + "-" + month + "-" + day + " " + hours + ":" + minutes + ":" + seconds + "." + milliseconds
	return formattedDateTime
}

var currentDateTime = getCurrentDateTime()
console.log(currentDateTime)    // 2023-08-29 23:22:34.665
```