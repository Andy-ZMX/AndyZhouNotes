
**把一大堆复杂的sql语句放在with as里面，取一个别名，后面的查询就可以用它，清晰明了**

```sql
with                          
a as (select * from machine),
b as (select * from machinespec)
select * from a, b where a.machinename = b.machinename
```
