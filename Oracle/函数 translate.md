
**字符替换，可以多换少，不能少换多**

```sql
select translate('Andy', 'A', 'a') from dual      -- andy
select translate('Andy', 'Ay', 'aY') from dual    -- andY 可以隔着替换
select translate('Andy', 'Andy', 'x') from dual   -- x
select translate('Andy', 'Andy', '') from dual    -- null
```