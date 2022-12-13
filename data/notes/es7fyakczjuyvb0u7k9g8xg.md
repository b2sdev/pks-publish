
## What

Delta table은 parquet 파일에 기능을 더한 Delta 파일에 또 기능을 추가한 것

### Delta Tables
    - Delta files
    - Registered in a metastore
    - Delta tractional logs

### Delta files
    - Data versioning
    - Transaction logs
    - ACID transactions

### Parquet files
    - Power to store tablular data
    - Fast
    - Columnar storage


## SQL examples

```sql
CREATE OR REPLACE TABLE table_name (
    id STRING,
    birthDate DATE,
    avgRating FLOAT
)

CREATE TABLE IF NOT EXISTS table_name (
    id STRING,
    birthDate DATE,
    avgRating FLOAT
)

SELECT DISTINCT * FROM my_table;
```