
**查看所有的存储过程：**

```sql
SELECT * FROM user_objects WHERE object_type = 'PROCEDURE'
```

**创建存储过程：**

```sql
CREATE OR REPLACE PROCEDURE ANDYTEST AS
  ID        VARCHAR2(100);
  EVENTTIME DATE;
BEGIN
  ID        := TO_CHAR(SYSDATE, 'yyyymmddhh24miss');
  EVENTTIME := SYSDATE;

  INSERT INTO CT_ANDYTEST
    (ID, NAME, EVENTTIME)
  VALUES
    (ID, 'Andy', EVENTTIME);
END;
```

**执行存储过程：**

```sql
BEGIN
  ANDYTEST();
  COMMIT;
END;
```