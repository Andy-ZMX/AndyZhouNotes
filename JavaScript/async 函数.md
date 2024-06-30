
---

**我现在想要装修房子，就得先去银行取钱，再用钱买材料，最后装修**

```javascript
function doSomething(params) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(params);
    }, 1000)
  })
}

function decorateHouse() {
  doSomething('取钱').then(res1 => {
    console.log(res1)
    doSomething('买材料').then(res2 => {
      console.log(res2)
      doSomething('装修').then(res3 => {
        console.log(res3)
      })
    })
  })
}

decorateHouse()    //先取1s钱，再买1s材料，最后装修1s
```

------------

**这样的代码不雅观，可以用 async/await 来代替：**

```javascript
function doSomething(params) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(params);
    }, 1000)
  })
}

async function decorateHouse() {
  let money = await doSomething('取钱')
  console.log(money)
  let material = await doSomething('买材料')
  console.log(material)
  let decoration = await doSomething('装修')
  console.log(decoration)
}

decorateHouse()    //也是先取1s钱，再买1s材料，最后装修1s
```

------------

**async/await 用来简化 Promise**
**特别注意：await 后面都是跟着 Promise 才会产生排队效果**
**语法糖关系：async/await —— Generator —— Promise**

```javascript
// Promise 写法
function fn() {
	Promise.resolve(getMoney()).then(() => getMateial())
}

// async/await 写法
async function fn() {
	await getMoney()
	await getMateial()
}
```

语法糖这个东西你就算不用他，你用其他手段也能达到这个东西同样的效果，但是可能就没有这个东西这么方便了（你走路也能走到北京，但是你坐飞机会更快到北京）

------------

**async 函数也可以有返回值，并且能用 then 输出：**

```javascript
function requestA(str) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(str)
      console.log(str)
    }, 1000)
  })
}
function requestB(str) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(str)
      console.log(str)
    }, 2000)
  })
}

async function fn() {
  await requestA("aaa")
  await requestB("bbb")

  return 999
}
fn().then(res => {
  console.log(res)    // 999
})
```

------------

**async 中只要有一个 await 命令后面的 Promise 的状态变为 reject，那么整个 async 函数都会中断执行：**

```javascript
function requestA(str) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      reject(str)
    }, 1000)
  })
}
function requestB(str) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(str)
    }, 2000)
  })
}

async function fn() {
  await requestA("aaa")
  console.log('2')
  await requestB("bbb")
  console.log('3')
  return 999
}
fn().then(res => {
  console.log(res)
})
```


------------

**新结构 try catch：为了防止由于 reject 之后不执行**

```javascript
function requestA(str) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      reject(str)
    }, 1000)
  })
}
function requestB(str) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(str)
    }, 2000)
  })
}

async function fn() {
  console.log('1')    // 1
  try { await requestA("aaa"); }
  catch { }
  console.log('2')    // 2
  try { await requestB("bbb"); }
  catch { }
  console.log('3')    // 3 
  return 999
}
fn().then(res => {
  console.log(res)    // 999
})
```

------------

https://juejin.cn/post/7007031572238958629




