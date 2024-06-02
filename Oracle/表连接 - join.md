
**join 和 inner join** 

```sql
-- 以下结果集相同
select * from a join b on a.name = b.name
select * from a inner join b on a.name = b.name
select * from a, b where a.name = b.name
```

------------

**left join**

```sql
-- 以下结果集相同
select * from a left join b on a.name = b.name
select * from a, b where a.name = b.name(+)
```

------------

**full join**

```sql
-- 可以通过查找产生 NULL 值的行，发现两个表之间存在的差异
select * from a full join b on a.name = b.name
```

------------

**cross join（笛卡尔积）**

```sql
-- 以下结果集相同
select * from a, b
select * from a cross join b
```