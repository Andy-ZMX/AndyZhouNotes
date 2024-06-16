
### ROWID
rowid是数据库中每一行数据的标识符（相当于base64编码的物理地址）
由四个部分组成：
- OOOOOO：数据对象编号（6位显示）
- FFF：相关数据文件编号（3位显示）
- BBBBBB：数据块编号（6位显示）
- RRR：数据块中行编号（3位显示）

```sql
SELECT ROWID,
       DBMS_ROWID.ROWID_OBJECT(ROWID) AS OBJECT,
       DBMS_ROWID.ROWID_RELATIVE_FNO(ROWID) AS FILENUM,
       DBMS_ROWID.ROWID_BLOCK_NUMBER(ROWID) AS BLOCK,
       DBMS_ROWID.ROWID_ROW_NUMBER(ROWID) AS ROWN
  FROM LOT
 WHERE LOTNAME = 'Z66722CE060117'
```
![[Pasted image 20240616160640.png]]

------------
### 聚簇因子 
聚簇因子（CLUSTERING_FACTOR）认为是根据索引遍历一遍实体表的逻辑读的块数。因为数据读取方式以块为单位，不是行，因此在读取大范围数据（满足条件行很多，不是unique index scan）时，利用聚簇因子好的索引，其读取块少，读取效率会很高
```sql
SELECT OWNER, INDEX_NAME, TABLE_NAME, UNIQUENESS, CLUSTERING_FACTOR
  FROM ALL_INDEXES
 WHERE OWNER = 'T1FEMADM'
   AND TABLE_NAME = 'LOT'
```
若聚簇因子大于表块的10倍左右，此索引就不能用了，不如用全表扫描，若聚簇因子和表块的大小很接近，此说明表有序
```sql
SELECT SEGMENT_NAME, BLOCKS
  FROM USER_SEGMENTS
 WHERE SEGMENT_TYPE = 'TABLE'
   AND SEGMENT_NAME = 'LOT'
```
先查索引叶节点，取每行得到rowid，再根据rowid去实体表中查询，但是聚簇因子很大的话，连续的rowid很随机，无法实现连续读取

------------
### TABLE ACCESS BY USER ROWID
直接通过 rowid 回表
![[Pasted image 20240616160702.png]]

------------
### TABLE ACCESS BY INDEX ROWID
通过 index 获取 rowid 再回表（仅一行）
![[Pasted image 20240616160722.png]]

------------
### TABLE ACCESS BY INDEX ROWID BATCHED
通过 index 获取 rowid（排个序）再回表（获取多个行的数据）
![[Pasted image 20240616160750.png]]

举个例子，以下有四行数据：
(1) 索引扫描返回需要回表的第一个记录rowid，假设对应到第一个数据文件、第一个数据块、第一行的数据。
(2) 索引扫描返回需要回表的第二个记录rowid，可能对应到第二个数据文件、第二个数据块、第一行的数据。
(3) 索引扫描返回需要回表的第三个记录rowid，假设对应到第一个数据文件、第一个数据块、第二行的数据。
(4) 索引扫描返回需要回表的第四个记录rowid，可能对应到第一个数据文件、第一个数据块、第三行的数据。

这个 BATCHED 的意思是在回表时，Oracle 会根据 rowid 排序，尽量按照顺序进行回表
上面的 (1)、(3)、(4) 的三次回表，可能要三次I/O ，现在批量回表，可能只需要一次I/O，降低了物理读

------------
### INDEX UNIQUE SCAN
索引唯一扫描
![[Pasted image 20240616160811.png]]

------------
### INDEX RANGE SCAN
索引范围扫描（where 条件中有索引引导列）
![[Pasted image 20240616160827.png]]


------------
### INDEX SKIP SCAN
索引跳跃扫描（where 条件中没有索引引导列，skip 可以理解为跳跃引导列的意思）
以下 PRODUCTREQUESTNAME, FACTORYNAME, LOTHOLDSTATE, LOTSTATE 为联合索引
![[Pasted image 20240616160843.png]]

------------
### INDEX FAST FULL SCAN
索引快速全扫描（select 后边都是索引列里的，并且 where 条件中没有索引引导列的）
以下 PRODUCTREQUESTNAME, FACTORYNAME, LOTHOLDSTATE, LOTSTATE 为联合索引
![[Pasted image 20240616160857.png]]

------------
### TABLE ACCESS FULL
全表扫描
以下 DISPATCHINGFLAG, FACTORYNAME 为联合索引，虽然 DISPATCHINGFLAG 为条件，但过滤性能不强，oracle 会放弃该索引
![[Pasted image 20240616160907.png]]

------------
### 查询索引
```sql
SELECT * FROM USER_INDEXES WHERE TABLE_NAME = 'LOT'
SELECT * FROM USER_IND_COLUMNS WHERE TABLE_NAME = 'LOT'
```

------------
### 创建索引
```sql
CREATE INDEX CT_FIRSTINSP_INDEX1 ON CT_FIRSTINSP(CREATETIME)
```