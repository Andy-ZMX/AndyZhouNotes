
---

**Where**

```csharp
// 查询 ADDRESS 为 XM 的人
BindingList<Person> list = new BindingList<Person>();
list.Add(new Person() { NAME = "Bruce", AGE = "19", ADDRESS = "XM" });
list.Add(new Person() { NAME = "Andy", AGE = "21", ADDRESS = "TL" });
list.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });

List<Person> result1 = list.Where(item => item.ADDRESS == "XM").ToList();
List<Person> result2 = (from item in list where item.ADDRESS == "XM" select item).ToList();
```

------------

**Select**

```csharp
// 查询所有人的 NAME
BindingList<Person> list = new BindingList<Person>();
list.Add(new Person() { NAME = "Bruce", AGE = "19", ADDRESS = "XM" });
list.Add(new Person() { NAME = "Andy", AGE = "21", ADDRESS = "TL" });
list.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });

var result1 = list.Select(item => item.NAME).ToList();
var result2 = (from item in list select item.NAME).ToList();
```

------------

**Order by**

```csharp
// 按照 AGE 升序排列
BindingList<Person> list = new BindingList<Person>();
list.Add(new Person() { NAME = "Bruce", AGE = "19", ADDRESS = "XM" });
list.Add(new Person() { NAME = "Andy", AGE = "21", ADDRESS = "TL" });
list.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });

var result1 = list.OrderBy(item => item.AGE).ToList();
var result2 = (from item in list orderby item.AGE select item).ToList();
```

```csharp
// 按照 AGE 降序排列
BindingList<Person> list = new BindingList<Person>();
list.Add(new Person() { NAME = "Bruce", AGE = "19", ADDRESS = "XM" });
list.Add(new Person() { NAME = "Andy", AGE = "21", ADDRESS = "TL" });
list.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });

var result1 = list.OrderByDescending(item => item.AGE).ToList();
var result2 = (from item in list orderby item.AGE descending select item).ToList();
```

------------

**join**

```csharp
// 串表 join
BindingList<Person> list1 = new BindingList<Person>();
list1.Add(new Person() { NAME = "Bruce", AGE = "19", ADDRESS = "XM" });
list1.Add(new Person() { NAME = "Andy", AGE = "21", ADDRESS = "TL" });
list1.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });

BindingList<Person> list2 = new BindingList<Person>();
list2.Add(new Person() { NAME = "Bruce", PHONE = "111111" });
list2.Add(new Person() { NAME = "Andy", PHONE = "222222" });
list2.Add(new Person() { NAME = "Curry" });

var result1 = list1.Join(list2, item1 => item1.NAME, item2 => item2.NAME, (item1, item2) => new { NAME = item1.NAME, PHONE = item2.PHONE }).ToList();
var result2 = (from item1 in list1
			   join item2 in list2 on item1.NAME equals item2.NAME
			   select new { NEME = item1.NAME, PHONE = item2.PHONE }).ToList();
```

------------

**in**

```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };  
List<int> filterList = new List<int> { 3, 4 };  
  
var result = numbers.Where(n => filterList.Contains(n));  
  
foreach (var num in result)  
{  
    Console.WriteLine(num); // Output: 3 and 4  
}
```

------------

**All 和 Any**

```csharp
BindingList<Person> list1 = new BindingList<Person>();
list1.Add(new Person() { NAME = "Bruce", AGE = "19", ADDRESS = "XM" });
list1.Add(new Person() { NAME = "Andy", AGE = "21", ADDRESS = "TL" });
list1.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });

var result1 = list1.All(item => item.ADDRESS == "XM");      // false
var result2 = list1.Any(item => item.ADDRESS == "XM");      // true
```

------------

**Union**

```csharp
BindingList<Person> list1 = new BindingList<Person>();
list1.Add(new Person() { NAME = "Bruce", AGE = "19", ADDRESS = "XM" });
list1.Add(new Person() { NAME = "Andy", AGE = "21", ADDRESS = "TL" });
list1.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });

BindingList<Person> list2 = new BindingList<Person>();
list2.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });
list2.Add(new Person() { NAME = "David", AGE = "19", ADDRESS = "XM" });
list2.Add(new Person() { NAME = "Frank", AGE = "21", ADDRESS = "TL" });

var result1 = list1.Union(list2).ToList();		// 结果为 6 条
var result2 = (from item1 in list1 select item1.NAME).Union(from item2 in list2 select item2.NAME).ToList();	// 结果为 5 条
```

------------

**Intersect**

```csharp
BindingList<Person> list1 = new BindingList<Person>();
list1.Add(new Person() { NAME = "Bruce", AGE = "19", ADDRESS = "XM" });
list1.Add(new Person() { NAME = "Andy", AGE = "21", ADDRESS = "TL" });
list1.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });

BindingList<Person> list2 = new BindingList<Person>();
list2.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });
list2.Add(new Person() { NAME = "David", AGE = "19", ADDRESS = "XM" });
list2.Add(new Person() { NAME = "Frank", AGE = "21", ADDRESS = "TL" });

var result1 = list1.Intersect(list2).ToList();		// 结果为 0 条
var result2 = (from item1 in list1 select item1.NAME).Intersect(from item2 in list2 select item2.NAME).ToList();	// 结果为 1 条
```

------------

**Skip 和 Take 分页**

```csharp
BindingList<Person> list2 = new BindingList<Person>();
list2.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });
list2.Add(new Person() { NAME = "Curry", AGE = "20", ADDRESS = "XM" });
list2.Add(new Person() { NAME = "David", AGE = "19", ADDRESS = "XM" });
list2.Add(new Person() { NAME = "Frank", AGE = "21", ADDRESS = "TL" });

var result1 = (from item in list2 select item).Skip(2).Take(1).ToList();
```

------------

https://learn.microsoft.com/zh-cn/dotnet/csharp/linq/
http://www.manongjc.com/detail/41-pizyzodvwbecpvz.html