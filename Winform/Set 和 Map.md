
---

```csharp
// set

HashSet<string> set = new HashSet<string>();
set.Add("Andy");
set.Add("Curry");
set.Add("Andy");
```

```csharp
// C# 的 Dictionary 相当于 Java 的 Map

Dictionary<string, string> dic = new Dictionary<string, string>();
dic.Add("name", "Andy");
dic.Add("age", "18");
Console.WriteLine(dic["name"]);        //Andy
```

```csharp
// 添加已经存在的键名会报错

Dictionary<string, string> dic = new Dictionary<string, string>();
dic.Add("name", "Andy1");
dic.Add("name", "Andy2");    // 报错
```

```csharp
// 判断dic中是否包含某个key

Dictionary<string, string> dic = new Dictionary<string, string>();
dic.Add("name", "Andy");
dic.Add("age", "18");
Console.WriteLine(dic.ContainsKey("name"));     // true
Console.WriteLine(dic.ContainsKey("address"));  // false
```

```csharp
// 根据key删除dic中元素

Dictionary<string, string> dic = new Dictionary<string, string>();
dic.Add("name", "Andy");
dic.Remove("name");
```


