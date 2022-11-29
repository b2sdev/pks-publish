---
id: vtzfkb3yhrdf403l7lqwan9
title: Constraint
desc: ''
updated: 1669725826531
created: 1669725232234
---

## 유효 기대값을 벗어나는 데이터 인입 처리

- Databricks의 Delta Live Tables에서는 아래와 같이 expectations clause를 정의하면, 기대값을 벗어나는 데이터는 target dataset에 추가됨과 동시에 event log에 invalid로 기록이 됨
```sql
CONSTRAINT valid_timestamp EXPECT (timestamp > '2022-01-01')
```