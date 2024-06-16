
```sql
select to_char(10.2345,'FM990.999') from dual   -- 10.235	四舍五入
select to_char(10.23,'FM990.990') from dual   -- 10.230
```

```sql
SELECT TO_CHAR(SYSDATE,'YYYY-MM-DD HH24:MI:SS') FROM DUAL
SELECT TO_CHAR(SYSTIMESTAMP,'YYYY-MM-DD HH24:MI:SS:FF9') FROM DUAL
```