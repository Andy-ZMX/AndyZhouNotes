
- 如果 参数1 不等于 参数2 ，那么返回 参数1
- 如果 参数1 等于 参数2 ，那么返回 null
- 参数1 和 参数2 数据类型必须相同

```sql
select nullif(1, 2) from dual		-- 1
select nullif(1, 1) from dual		-- null
```
