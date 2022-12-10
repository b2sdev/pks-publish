---
id: hvd8818q6qo5xxfok5lhye7
title: Delta Live Tables
desc: ''
updated: 1670635956880
created: 1669724994686
---

## What
- Automated data pipelines for Delta Lake <-- [[dev.data+ai.databricks.delta_table]] + [[dev.data+ai.spark.structured_streaming]]
- 데이터 처리 파이프라인을 빌드하기 위한 프레임워크
- 사용자는 데이터에 대해 수행할 변환을 정의하고, DLT는 작업 오케스트레이션, 클러스터 관리, 모니터링, 데이터 품질 및 오류 처리를 관리
- 여러 Spark 작업을 사용하여 데이터 파이프라인을 정의하는 대신 DLT는 각 처리 단계에 대해 사용자가 정의하는 대상 스키마를 기반으로 데이터를 변화하는 방법을 관리
- DLT는 기대치를 사용하여 데이터 품질을 적용할 수도 있음
  - 예상 데이터 품질을 정의하고 이러한 기대에 실패한 레코드를 처리하는 방법을 지정할 수 있음 ([[dev.data+ai.data_ingestion.constraint]])

## How

### Data Ingestion
  - Cloud storage에 있는 data: `Auto Loader`를 사용하여 데이터가 업로드될 때마다 Delta Live Table이 ingest
  ```python
spark.readStream.format('cloudFiles') # enables the use of Auto Loader
     .option("cloudFiles.format", "csv")
     .load("path/to/customers")
  ```

  - `Append-only` 속성을 가지는 다른 delta table: `SQL STREAM()` function을 사용하여 ingest

### Delta live table 생성
```sql
CREATE LIVE TABLE customers
AS SELECT * FROM cloud_files(...)
```


### Streaming data processing

#### Python
```python
@dlt.table
def streaming_bronze():
  return (
    # Since this is a streaming source, this table is incremental.
    spark.readStream.format("cloudFiles")
      .option("cloudFiles.format", "json")
      .load("abfss://path/to/raw/data")
  )

@dlt.table
def streaming_silver():
  # Since we read the bronze table as a stream, this silver table is also
  # updated incrementally.
  return dlt.read_stream("streaming_bronze").where(...)

@dlt.table
def live_gold():
  # This table will be recomputed completely by reading the whole silver table
  # when it is updated.
  return dlt.read("streaming_silver").groupBy("user_id").count()
```

#### SQL
```sql
CREATE OR REFRESH STREAMING LIVE TABLE streaming_bronze
AS SELECT * FROM cloud_files(
  "abfss://path/to/raw/data", "json"
)

CREATE OR REFRESH STREAMING LIVE TABLE streaming_silver
AS SELECT * FROM STREAM(LIVE.streaming_bronze) WHERE...

CREATE OR REFRESH LIVE TABLE live_gold
AS SELECT count(*) FROM LIVE.streaming_silver GROUP BY user_id
```

### 

```python
# from a Bronze table to a Silver table
(spark.table("sales")
    .withColumn("avg_price", col("sales") / col("units")))
    .writeStream
    .option("checkpointLocation", checkpointPath)
    .outputMode("append)
    .table("cleanedSales")
```

```Python
(spark.table("sales")
    .withColumn("avg_price", col("sales") / col("units")))
    .writeStream
    .option("checkpointLocation", checkpointPath)
    .output("complete")
    .trigger(once=True)
    .table("new_sales")
```

## Medalion Structures

![](https://www.databricks.com/wp-content/uploads/2022/03/delta-lake-medallion-architecture-2.jpeg)
- Data source > Bronze
    - A job that ingests raw data from a streaming source into the Lakehouse
- Bronze > Silver
    - A job that enriches data by parsing its timestamps into a human-readable format
- Silver > Gold
    - A job that queries aggregated data to publish key insights into a dashboard
    - A job that develops a feature set for a machine learning application
    - A job that aggregates cleaned data to create standard summary statistics

- https://www.databricks.com/glossary/medallion-architecture