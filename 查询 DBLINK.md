
**查询所有 同义词 和 DBLINK 的关系：**

```sql
SELECT * FROM USER_SYNONYMS
```

![[Pasted image 20240702214506.png]]

------------

**通过同义词查询：**

```sql
SELECT * FROM ADS_LOT_AUTO_F_INSP_TO_MES
```

![[Pasted image 20240702214518.png]]

------------

**通过DBLINK查询：**

```sql
SELECT * FROM T1EDBADM.ADS_LOT_F_CHECK_STATE@DBLK_EDB
```

![[Pasted image 20240702214531.png]]