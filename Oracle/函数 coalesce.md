
**返回第一个不为 null 的值，如果都为 null，最终返回 null（这些参数的数据类型必须一致）**

```sql
select coalesce(null, null, 1, 2) from dual       -- 1
select coalesce(null, '', '1', '2') from dual     -- 1
```