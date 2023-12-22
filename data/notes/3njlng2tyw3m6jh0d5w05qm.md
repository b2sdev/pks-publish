
## 한 주 전 날짜 구하기 (KST)

```sql
DECLARE @today VARCHAR(10)
DECLARE @1weekago VARCHAR(10)
SET @today = CONVERT(DATE, DATEADD(HOUR, 9, GETDATE())) -- 2022-11-23
SET @1weekago = CONVERT(DATE, DATEADD(DAY, -6, @today)) -- 2022-11-17
PRINT(@today)
PRINT(@1weekago)
```