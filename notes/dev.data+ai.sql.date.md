---
id: 3njlng2tyw3m6jh0d5w05qm
title: SQL로 날짜 다루기
desc: ''
updated: 1669210269640
created: 1669210001219
---

## 한 주 전 날짜 구하기 (KST)

```sql
DECLARE @today VARCHAR(10)
DECLARE @1weekago VARCHAR(10)
SET @today = CONVERT(DATE, DATEADD(HOUR, 9, GETDATE())) -- 2022-11-23
SET @1weekago = CONVERT(DATE, DATEADD(DAY, -6, @today)) -- 2022-11-17
PRINT(@today)
PRINT(@1weekago)
```