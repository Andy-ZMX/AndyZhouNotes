
** WeakMap 和 Map 的区别：**
- 键的类型：WeakMap 的键只能为 对象 和 Symbol，Map 的键可以是任意值
- 属性方法：WeakMap 没有size属性，没有遍历方法，没有 clear 方法
- WeakMap 的键名所指向的对象，不会阻止垃圾回收

------------

** 只有四个方法**

- WeakMap.prototype.set()
- WeakMap.prototype.get()
- WeakMap.prototype.has()
- WeakMap.prototype.delete()