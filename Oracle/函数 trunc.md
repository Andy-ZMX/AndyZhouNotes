
**舍去小数点**
```sql
select trunc(12345.67,0) from dual    -- 12345		舍去小数点
select trunc(12345.67,1) from dual    -- 12345.6	舍去小数点后一位
select trunc(12345.67,-1) from dual   -- 12340		舍去小数点前一位
```
