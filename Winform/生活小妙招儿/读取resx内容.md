
---

```csharp
using System.Resources;
using System.Reflection;

ResourceManager rm = new ResourceManager("WindowsFormsApp1.Properties.Andy.Test.Resources", Assembly.GetExecutingAssembly());
string name = rm.GetString("name");
```

![[Pasted image 20240819221748.png]]