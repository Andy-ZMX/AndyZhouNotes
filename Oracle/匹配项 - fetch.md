
**只匹配前10条**

```sql
select * from machinespec where detailmachinetype = 'Main'
fetch first 10 rows only
```

------------

**匹配前10条，如果第10条的 machinegroupname 为 CVD，接下来的3条的 machinegroupname 也是CVD
那么返回的结果就是13条（必须指定 order by）**

```sql
select * from machinespec where detailmachinetype = 'Main' and machinegroupname = 'CVD'
order by machinegroupname
fetch first 10 rows with ties
```

------------

**跳过前10条**

```sql
select * from machinespec where detailmachinetype = 'Main'
offset 10 rows
```

------------

**跳过前10条，只查询接下来的两条**

```sql
-- 这个功能可以用于分页的实现
select * from machinespec where detailmachinetype = 'Main' and machinegroupname = 'PVD'
offset 10 rows 
fetch next 2 rows only
```
