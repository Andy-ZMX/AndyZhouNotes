
**递归查询 主机下面所有的腔室**

```sql
SELECT *
    FROM MACHINESPEC
   START WITH MACHINENAME = :MACHINENAME
  CONNECT BY PRIOR MACHINENAME = SUPERMACHINENAME
```

------------

https://www.cnblogs.com/zyzdisciple/p/7873584.html