
参数等于 0，返回 0
参数小于 0，返回 -1
参数大于 0，返回 +1

```sql
select age, sign(age - 20) from test_andy
```

与 decode 搭配 有奇效