
---

**引用调用：ref**

```csharp
static void Main(string[] args)
{
	int a = 0;  // 必须在这里初始化赋值
	int b = 0;

	myFunction(ref a, ref b);

	Console.WriteLine(a);   // 1
	Console.WriteLine(b);   // 2
}
public static void myFunction(ref int x, ref int y)
{
	Console.WriteLine(x);   // 0
	Console.WriteLine(y);   // 0
	x = 1;
	y = 2;
}
```

------------

**引用调用：out**

```csharp
static void Main(string[] args)
{
	int a = 0;  // 初始化值没有用
	int b = 0;

	myFunction(out a, out b);

	Console.WriteLine(a);   // 1
	Console.WriteLine(b);   // 2
}
public static void myFunction(out int x, out int y)
{
	x = 1;  // 必须在这里赋值
	y = 2;
}
```