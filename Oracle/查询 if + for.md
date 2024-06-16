
```sql
declare
  grade varchar2(2) := 'b';
begin
  for item in (select * from test_andy) loop
    if item.age > 20 then
      dbms_output.put_line('excellent');
    elsif item.age < 20 then
      dbms_output.put_line('not bad');
    else
      dbms_output.put_line('good');
    end if;
  end loop;
end;
```

```sql
DECLARE
  SEQ NUMBER := 1;
BEGIN
  FOR ITEM IN (SELECT SEQ + 1 AS SEQ
                 FROM (SELECT SEQ
                         FROM CT_DSPRESERVE
                        WHERE MACHINENAME = :MACHINENAME
                          AND SEQ > 0
                        ORDER BY SEQ DESC)
                WHERE ROWNUM = 1) LOOP
    SEQ := ITEM.SEQ;
  END LOOP;
  INSERT INTO CT_DSPRESERVE
    (LOTNAME, OPERATIONNAME, MACHINENAME, SEQ, EVENTTIME, EVENTUSER)
  VALUES
    (:LOTNAME, :OPERATIONNAME, :MACHINENAME, SEQ, SYSDATE, 'AUTO');
END
```

```sql
declare
      LOTNAME              VARCHAR2(100);
      CSTID                VARCHAR2(100);
      ABNORMALTYPE         VARCHAR2(100);
      DEPARTMENT           VARCHAR2(100);
      PROCESSOPERATIONNAME VARCHAR2(100);
      PROCESSOPERATIONDESC VARCHAR2(100);
      STAYTIME             VARCHAR2(100);
      PROCESSSTATE         VARCHAR2(100);
      HOLDFLAG             VARCHAR2(100);
      DSPFLAG              VARCHAR2(100);
begin      
     for item in (SELECT * FROM CT_ABNORMALLOT) loop
         LOTNAME := item.LOTNAME;
         CSTID := item.CSTID;
         ABNORMALTYPE := item.ABNORMALTYPE;
         DEPARTMENT := item.DEPARTMENT;
         PROCESSOPERATIONNAME := item.PROCESSOPERATIONNAME;
         PROCESSOPERATIONDESC := item.PROCESSOPERATIONDESC;
         STAYTIME := item.STAYTIME;
         PROCESSSTATE := item.PROCESSSTATE;
         HOLDFLAG := item.HOLDFLAG;
         DSPFLAG := item.DSPFLAG;
         INSERT INTO CT_ABNORMALLOTHIS (PROCESSSTATE,HOLDFLAG,DSPFLAG,EVENTNAME,EVENTTIME,EVENTUSER)VALUES(PROCESSSTATE,HOLDFLAG,DSPFLAG,:EVENTNAME,TO_DATE(:EVENTTIME, 'yyyy-mm-dd hh24:mi:ss'),:EVENTUSER);
      end loop; 
      commit;   
end;
```