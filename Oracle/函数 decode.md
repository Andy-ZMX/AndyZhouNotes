
**三个参数：相当于一个 case**
```sql
select version,
       description,
       decode(version, '00001', '这是第一代'),
       decode(description, 'Andy', '这是Andy的')
  from ct_customddl
```

------------

**五个参数：相当于两个 case**
```sql
select version,
       description,
       decode(version, '00001', '这是第一代', '00002', '这是第二代')
  from ct_customddl
```

------------

**四个参数：相当于一个 case 和 一个默认值**
```sql
select version, 
       description, 
       decode(version, '00001', '这是第一代', '其它')
  from ct_customddl
```

