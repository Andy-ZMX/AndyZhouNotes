
---

**新建文件：andy.reg**
**双击执行**

```shell
Windows Registry Editor Version 5.00
[HKEY_CLASSES_ROOT\andy]
@="URL:myWebshell Protocol Handler"
"URL Protocol"=""
[HKEY_CLASSES_ROOT\andy\DefaultIcon]
@="C:\\Users\\mingxin_zhou1\\AppData\\Local\\Postman\\Postman.exe"
[HKEY_CLASSES_ROOT\andy\shell]
[HKEY_CLASSES_ROOT\andy\shell\open]
[HKEY_CLASSES_ROOT\andy\shell\open\command]
@="\"C:\\Users\\mingxin_zhou1\\AppData\\Local\\Postman\\Postman.exe\" \"%1\""
```

```html
<a href="andy://open">打开 postman </a>
```