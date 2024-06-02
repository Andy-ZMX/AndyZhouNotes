
**以下 sql 将返回 ct_customquery 的所有数据**

```sql
select * from ct_customquery where description = 'Andy' and exists(select * from dual where rownum = 1)
```

------------

**以下 sql 将返回 null**

```sql
select * from ct_customquery where description = 'Andy' and exists(select * from dual where rownum = 0)
```

------------

**子查询的where条件中，如果有关于外边a表的条件，整个 sql 的结果都会被其影响**

```sql
select count(1) from lot a where exists(select * from product b where a.lotname = b.lotname)  -- 1787
select count(1) from lot -- 2470
```