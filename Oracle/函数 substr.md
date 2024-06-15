```sql
select substr('abcdefg',3) from dual    -- cdefg	表示从第3个字符开始截取到最后（不是从0开始计数）
select substr('abcdefg',2,3) from dual  -- bcd		表示从第2个字符开始，一共3个字符
```
