---
id: okqv7bt20hfz93cqagtcykh
title: Pandas로 SQL 쿼리
desc: ''
updated: 1669209279973
created: 1669208447453
---

## SQL Query

```python
user_id = "user001"
query = f"SELECT * FROM user_info WHERE id='{user001}'"
pd.read_sql(query, cnxn)
```

## Stored Procedure

[[dev.cs.database.stored-procedure]]를 호출하려면 `read_sql_query`를 사용한다.

```python
user_id = "user001"
query = "EXEC dbo.sp_getUserInfo @id='{user_id}'"
pd.read_sql_query(query, cnxn)
```
