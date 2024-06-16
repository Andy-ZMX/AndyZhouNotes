
```sql
-- 2
SELECT XMLQUERY('//SORTINGJOBLIST/SORTINGJOB/SORTINGPRODUCTLIST/SORTINGPRODUCT[1]/SOURCEPOSITION/text()' PASSING XMLTYPE(MESSAGELOG) RETURNING CONTENT).GETSTRINGVAL() AS NAME
  FROM CT_MESSAGELOG
 WHERE EVENTTIMEKEY = '20240507191517244000'
```

![[Pasted image 20240616150407.png]]


```xml
<ENVELOP>
    <Header>
        <SourceSubject />
        <OriginalSourceSubject>_INBOX.0A6AB467.5FB86638671B11933F10.7298</OriginalSourceSubject>
        <TargetSubject>XMTM.TM18.TST.FEM.CNMsvr</TargetSubject>
        <ReplySubject>_INBOX.0A6AB467.5FB86638671B11933F10.7298</ReplySubject>
        <NAME>ONLINE_OFFLINE_OA_REQUEST</NAME>
        <TransactionId>20240507191515008926</TransactionId>
        <LOCALE>English</LOCALE>
        <TibrvMsgFormat>true</TibrvMsgFormat>
    </Header>
    <DataLayer>
        <SORTINGJOBLIST>
            <SORTINGJOB>
                <SOURCECSTNAME>CA0269</SOURCECSTNAME>
                <SOURCELOTNAME>Z667234D120</SOURCELOTNAME>
                <TARGETLOTNAME />
                <TARGETCSTNAME>SCRAP_CST</TARGETCSTNAME>
                <SORTINGPRODUCTLIST>
                    <SORTINGPRODUCT>
                        <SOURCEPOSITION>2</SOURCEPOSITION>
                        <PRODUCTNAME>Z667234D1202</PRODUCTNAME>
                        <TARGETPOSITION>2</TARGETPOSITION>
                    </SORTINGPRODUCT>
                    <SORTINGPRODUCT>
                        <SOURCEPOSITION>4</SOURCEPOSITION>
                        <PRODUCTNAME>Z667234D1204</PRODUCTNAME>
                        <TARGETPOSITION>4</TARGETPOSITION>
                    </SORTINGPRODUCT>
                    <SORTINGPRODUCT>
                        <SOURCEPOSITION>5</SOURCEPOSITION>
                        <PRODUCTNAME>Z667234D1205</PRODUCTNAME>
                        <TARGETPOSITION>5</TARGETPOSITION>
                    </SORTINGPRODUCT>
```