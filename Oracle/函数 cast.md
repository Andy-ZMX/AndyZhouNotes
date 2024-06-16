
**用于数据类型的转换，四舍五入：**

```sql
select cast(12.34 as int) from dual           -- 12
select cast(12.5 as int) from dual            -- 13
select cast('12.5' as int) from dual          -- 13
```