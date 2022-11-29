---
id: yfg1zp70ww391hvbdd4sgop
title: Databricks SQL
desc: ''
updated: 1669727432610
created: 1655698565248
---

## Databricks SQL

- 데이터 레이크에서 빠른 임시 SQL을 실행할 수 있음
- 쿼리 결과에 대한 다양한 시각화를 지원

## SQL 엔드포인트

- Databricks SQL 내의 데이터 개체에서 SQL 명령을 실행할 수 있는 계산 리소스
    - Azure Databricks 컴퓨팅 리소스의 한 유형

## SQL Reference

```sql
-- 데이터베이스 생성
CREATE DATABASE IF NOT EXISTS customer360 LOCATION '/customer/customer360';

-- 테이블 생성
CREATE TABLE my_table (id STRING, value STRING);

CREATE OR REPLACE TABLE table_name (
    id STRING,
    birthDate DATE,
    avgRating FLOAT
)

CREATE TABLE customersPerCountry AS
SELECT country,
       COUNT(*) AS customers
FROM customerLocations
GROUP BY country;

-- 사용자에게 권한 부여
GRANT ALL PRIVILEAGES ON TABLE sales TO new.engineer@company.com;
GRANT SELECT ON TABLE sales TO new.engineer@company.com;

-- 중복 제거
SELECT DISTINCT * FROM my_table;

-- unnest
-- card_id STRING, items ARRAY<item_id:STRING> --> card_id STRING, item_id STRING
SELECT cart_id, explode(items) AS item_id FROM raw_table;

-- extract
-- transaction_id STRING, payload ARRAY<customer_id:STRING, date:TIMESTAMP, store_id:STRING>
-- --> transacction_id: STRING, date TIMESTAMP
SELECT transaction_id, payload.date FROM raw_table;
```

