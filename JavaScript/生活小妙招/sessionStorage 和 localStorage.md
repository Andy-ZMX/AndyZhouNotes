
**区别：**
1、localStorage没有过期时间，适用于持久化存储需要在多个会话中共享的数据
2、sessionStorage针对一个session进行数据存储，生命周期与session相同，当用户关闭浏览器后，数据将被删除

```javascript
localStorage.setItem("name", "Andy")
localStorage.getItem("name")
localStorage.removeItem("name")
```

---

https://juejin.cn/post/7248623545219825723
