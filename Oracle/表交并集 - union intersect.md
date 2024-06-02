
**两个集合必须结构一样**

------------

**union**
将两个 sql 的结果取并集，并且去重（即使a表内部本身就有重复的数据也会去重）
```sql
select * from a
union
select * from b
```

------------

**union all**
将两个 sql 的结果取并集 ，不去重

```sql
select * from a
union all
select * from b
```

------------

**intersect**
将两个 sql 的结果取交集

```sql
select * from a
intersect
select * from b
```

------------

**minus**
A 去掉 A、B 的交集

```sql
select * from A minus select * from B
```
