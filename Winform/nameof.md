
---

**应用场景**

- 如果类的属性有修改，在编译的时候就可以提示报错了
- 用于获取属性的名称

```csharp
private void setGridHeader()
{
	GridHeaders head = new GridHeaders();
	head.AddGridColumn(nameof(CT_RISKWORECIVEPLAN.CHECKBOX), Language.GetLabel("Sel"), 40);
	head.AddGridColumn("PRODUCTNAME", Language.GetLabel("Risk 玻璃"), 80);
	head.AddGridColumn("TOFACTORY", Language.GetLabel("To 厂别"), 80);
	grdList.SetColumns(head);
}
```