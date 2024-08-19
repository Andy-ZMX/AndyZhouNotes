
---

**正常情况下：**

调用两个很耗时的函数，整个页面渲染下来大概需要 20s，并且期间页面卡住了

```javascript
<template>
  <button @click="printComment">print comment</button>
</template>

<script setup>

sendWorker1()
sendWorker2()
console.log("main thread")

function sendWorker1() {
  let sum = 0
  for (let i = 0; i < 20000; i++) {
    for (let i = 0; i < 20000; i++) {
      sum += Math.random()
    }
  }
  console.log("worker 1 thread finished")  // about 4s
}

function sendWorker2() {
  let sum = 0
  for (let i = 0; i < 40000; i++) {
    for (let i = 0; i < 40000; i++) {
      sum += Math.random()
    }
  }
  console.log("worker 2 thread finished")  // about 15s
}

</script>
```

------------

**使用 webworker 一共耗时 15s，并且不会阻塞主线程，先打印 main thread**

- 0s main thread
- 4s worker 1 thread
- 15s worker 2 thread

```javascript
npm install --save-dev worker-loader
```

```javascript
// main
<template>
  <button @click="printComment">print comment</button>
</template>
 
<script setup>
import { ref } from 'vue'

const worker1 = ref(null)
const worker2 = ref(null)

worker1.value = new Worker(new URL('@/my-worker-1.js', import.meta.url))
worker2.value = new Worker(new URL('@/my-worker-2.js', import.meta.url))

sendWorker1()
sendWorker2()
console.log("main thread")

function sendWorker1() {
  worker1.value.postMessage("start 1")
  worker1.value.onmessage = (e) => {
    console.log('vue: received ', e.data)
  }
}

function sendWorker2() {
  worker2.value.postMessage("start 2")
  worker2.value.onmessage = (e) => {
    console.log('vue: received ', e.data)
  }
}
</script>
```
```javascript
// my-worker-1.js
self.onmessage = () => {
  let sum = 0
  for (let i = 0; i < 20000; i++) {
    for (let i = 0; i < 20000; i++) {
      sum += Math.random()
    }
  }
  self.postMessage("worker 1 thread finished")  // about 4s
}
```
```javascript
// my-worker-2.js
self.onmessage = () => {
  let sum = 0
  for (let i = 0; i < 40000; i++) {
    for (let i = 0; i < 40000; i++) {
      sum += Math.random()
    }
  }
  self.postMessage("worker 2 thread finished")  // about 15s
}
```

------------

**main 和 worker 传值：**
```javascript
<template>
  <button @click="printComment">print comment</button>
</template>
 
<script setup>
import { ref } from 'vue'

const worker1 = ref(null)

sendWorker1()

function sendWorker1() {
  worker1.value = new Worker(new URL('@/my-worker-1.js', import.meta.url))
  worker1.value.postMessage({ name: "Andy", age: 24 })
  worker1.value.onmessage = (e) => {
    console.log('main received ', e.data)
  }
}
</script>
```
```javascript
self.onmessage = function (event) {
  console.log('worker received ', event.data)
  let result = event.data
  result.age++
  postMessage(result)
}
```

------------

https://juejin.cn/post/7340636105765535796