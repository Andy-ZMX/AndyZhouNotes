
**case when 放在 select 后**

```sql
select description,
       (case
         when description = 'Andy' then
          'ANDY'
         else
          'OTHERS'
       end) transform
  from ct_customquery
```

------------

**case when 放在 where 后，作为多条件筛选**

```sql
SELECT *
  FROM STUDENT
 WHERE (CASE
         WHEN AGE = 18 AND SEX = 'male' THEN
          1
         WHEN AGE = 19 AND SEX = 'female' THEN
          2
         ELSE
          0
       END) = 1
```