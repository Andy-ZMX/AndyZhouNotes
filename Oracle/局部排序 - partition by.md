
**先按 description 分组，再按 queryid 降序排序，sequence 与每组的长度有关**

```sql
select queryid,
       description,
       row_number() over(partition by description order by queryid desc) sequence
  from ct_customquery
```
