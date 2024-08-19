
---

**App.config**

```csharp
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7.2" />
    </startup>
	<appSettings>
		<add key="NAME" value="Andy"/>
	</appSettings>
</configuration>
```

------------

**CS文件读取方法1：**

```csharp
using System.Configuration;
string name = ConfigurationManager.AppSettings["NAME"];
```

------------

**CS文件读取方法2：**

```csharp
Configuration config = ConfigurationManager.OpenExeConfiguration(ConfigurationUserLevel.None);
string name = config.AppSettings.Settings["NAME"].Value;
```