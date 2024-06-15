
**如果 参数1 为空，就返回 参数2**
```sql
select nvl(null, 'Andy') from dual       -- Andy
select nvl('', 'Andy') from dual         -- Andy
select nvl('lalala', 'Andy') from dual   -- lalala
```

------------

**如果 参数1 为空，就返回 参数3：
如果 参数1 不为空，就返回 参数2：**
```sql
select nvl2(null, 'Andy1', 'Andy2') from dual           -- Andy2
select nvl2('', 'Andy1', 'Andy2') from dual             -- Andy2
select nvl2('lalala', 'Andy1', 'Andy2') from dual       -- Andy1
```

