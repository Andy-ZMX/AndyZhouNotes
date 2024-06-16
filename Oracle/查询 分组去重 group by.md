
**对结果分组，统计数量**

```sql
select lasteventcomment, count(1) as num from machine group by lasteventcomment
```

------------

**使用 having 增加条件**

```sql
select lasteventcomment, count(1) as num from machine where ROWNUM <= 10 group by lasteventcomment having count(1) < 3
```

------------

**where 和 having 的区别：**

- where 子句用于行条件筛选，having 子句用于分组后筛选
- having 一般都是配合 group by 和 聚合函数一起出现，如(count(), sum(), avg(), max(), min())
- where 子句中不能使用聚集函数，而 having 子句就可以

```sql
select count(1), sum(age) from andy_test group by name
```

---

**聚合函数**

```sql
-- 平均数
select avg(score) from student

-- 最大值
select max(score) from student

-- 最小值
select min(score) from student

-- 求和
select sum(score) from student

-- 行数
select count(1) from student
select count(address) from student	// 查询address不为空的行数 自动过滤掉null的数据
```