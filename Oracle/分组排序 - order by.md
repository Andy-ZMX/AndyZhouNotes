**分组排序**

```sql
select machinename, lasteventcomment from machine order by lasteventcomment
```

------------

**也可以直接写数字，表示 select 后的第几列**

```sql
select machinename, lasteventcomment from machine order by 2
```

------------

**按子串排序**

```sql
select substr(machinename, 0, 1), machinename, lasteventcomment from machine order by 1
```

------------

**DESC 降序排列，默认是 ASC 升序排列**

```sql
select machinename, lasteventcomment from machine order by lasteventcomment DESC
```

------------

**多字段排序，先排前边的**

```sql
select machinename, lasteventcomment from machine order by machinename ASC, lasteventcomment DESC
```

------------

**正序排序时 nul默认排在后边，可以使用 nulls first 关键字**

```sql
select * from ct_customquery order by description nulls first
select * from ct_customquery order by description desc nulls last
```