
**方法1：自定义组件**

```javascript
<template>
  input自动获取焦点：
  <input v-focus type="text">
</template>
  
<script setup>
const vFocus = {
  mounted: (el) => el.focus()
}
</script>

```

------------

**方法2：利用 nextTick**

```javascript
<template>
  input自动获取焦点：
  <input ref="inputdom" type="text">
</template>

<script setup>
import { nextTick, onMounted, ref } from "vue";
const inputdom = ref(null)

onMounted(() => {
  nextTick(() => {
    inputdom.value.focus();
  });
})
</script>
```

