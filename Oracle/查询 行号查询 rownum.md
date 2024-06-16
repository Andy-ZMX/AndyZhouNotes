
**使用 rownum 字段**

```sql
select rownum, a.* from ct_customddl a
```

------------

**使用 order by 会将其顺序打乱**

```sql
select rownum, a.* from ct_customddl a order by description
```

------------

**可以使用嵌套来解决**

```sql
select rownum, b.*
  from (select a.* from ct_customddl a order by description) b
```

------------

**查询指定行数**

```sql
select * from ct_customddl where rownum <= 3
```
