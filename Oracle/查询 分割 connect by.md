
**字符串分割：**

```sql
    select REGEXP_SUBSTR('01/02/03/04', '[^/]+', 1, rownum) as name
      from dual
    connect by rownum <= REGEXP_COUNT('01/02/03/04', '[^/]+')
```
```sql
SELECT REGEXP_SUBSTR('312CR4/3126R4/313CR3/666', '[^/]+', 1, ROWNUM) AS SEUSERID
    FROM DUAL
  CONNECT BY ROWNUM <=
             LENGTH('312CR4/3126R4/313CR3/666') -
             LENGTH(REGEXP_REPLACE('312CR4/3126R4/313CR3/666', '/', '')) + 1
```

------------

**获取1到10：**
```sql
select level from dual connect by level <= 10
```

------------

https://zhuanlan.zhihu.com/p/614242016