
## Databricks SQL

- 데이터 레이크에서 빠른 임시 SQL을 실행할 수 있음
- 쿼리 결과에 대한 다양한 시각화를 지원

## SQL 엔드포인트

- Databricks SQL 내의 데이터 개체에서 SQL 명령을 실행할 수 있는 계산 리소스
    - Azure Databricks 컴퓨팅 리소스의 한 유형

## Overwriting a table vs Deleting and Recreating a table
- Overwriting a table is eficient because no files need to be deleted.
- Overwriting a table maintains the old version of the table for Time Travel.
- Overwriting a table is an atomic operation and will not leave the table in an unfinished state.
- Overwriting a table allows for concurrent queries to be completed while in progress.

## SQL Reference

### 데이터베이스 생성
```sql
CREATE DATABASE IF NOT EXISTS customer360 LOCATION '/customer/customer360';
```

### 테이블 생성

```sql
CREATE TABLE my_table (id STRING, value STRING);

CREATE OR REPLACE TABLE table_name (
    id STRING,
    birthDate DATE,
    avgRating FLOAT
)
```

`CREATE OR REPLACE TABLE`
- 테이블이 없으면 새로 생성
- 테이블이 있으면 테이블을 리셋
> Delta Lake Table을 dropping하고 re-creating하는 것보다 REPLACE 명령을 사용할 것

`CREATE TABLE IF NOT EXISTS`
- 테이블이 있으면 테이블이 생성되지 않고 명령이 무시됨


```sql
CREATE TABLE customersPerCountry AS
SELECT country,
       COUNT(*) AS customers
FROM customerLocations
GROUP BY country;
```

```sql
-- Createa a CSV table from an external directory
CREATE TABLE student USING CSV LOCATION '/mnt/csv_files';
```

### 사용자에게 권한 부여
```sql
GRANT ALL PRIVILEAGES ON TABLE sales TO new.engineer@company.com;
GRANT SELECT ON TABLE sales TO new.engineer@company.com;
```

### 중복 제거
```sql
SELECT DISTINCT * FROM my_table;
```

### Upsert
To insert or update. If the item does not exist, add or insert it; if the item already exists, then update it with new information.

- `MERGE SQL` operation : upsert data from a source table, view, or DataFrame into a target Delta table (supported only for Delta Lake tables)
    - 만약 id가 있으면 -> to update rows
    - id가 없으면 -> to insert new rows

```sql
MERGE INTO people10m
USING people10mupdates
ON people10m.id = People10mupdates.id
WHEN MATCHED THEN
  UPDATE SET
    id = people10mupdates.id,
    firstName = people10mupdates.firstName,
    ssn = people10mupdates.ssn
WHEN NOT MATCHED
  THEN INSERT (
    id,
    firstName,
    ssn
  )
  VALUES (
    people10mupdates.id,
    people10mupdates.firstName,
    people10mupdates.ssn
  )
```

### Window functions

```sql
SELECT
    name
  , dept
  , salary
  , RANK() OVER (PARTITION BY dept ORDER BY salary) AS rank
  , DENSE_RANK() OVER (PARTITION BY dept ORDER BY salary) AS dense_rank
  , DENSE_RANK() OVER (PARTITION BY dept ORDER BY salary
                       ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS dense_rank2
  , MIN(salary) OVER (PARTITION BY dept ORDER BY salary) AS min
  , LAG(salary) OVER (PARTITION BY dept ORDER BY salary) AS lag
  , LEAD(salary, 1, 0) OVER (PARTITION BY dept ORDER BY salary) AS lead
FROM employees
;
```
![](/assets/images/sql_result_window_functions.png)

### TBD
```sql
-- unnest
-- card_id STRING, items ARRAY<item_id:STRING> --> card_id STRING, item_id STRING
SELECT cart_id, explode(items) AS item_id FROM raw_table;

-- extract
-- transaction_id STRING, payload ARRAY<customer_id:STRING, date:TIMESTAMP, store_id:STRING>
-- --> transacction_id: STRING, date TIMESTAMP
SELECT transaction_id, payload.date FROM raw_table;
```

## Reference
- [Upsert into a Delta Lake table using merge](https://docs.databricks.com/delta/merge.html)
- [CREATE TABLE [USING]](https://docs.databricks.com/sql/language-manual/sql-ref-syntax-ddl-create-table-using.html)
- [MERGE INTO](https://docs.databricks.com/sql/language-manual/delta-merge-into.html)
- [Window functions](https://docs.databricks.com/sql/language-manual/sql-ref-window-functions.html)