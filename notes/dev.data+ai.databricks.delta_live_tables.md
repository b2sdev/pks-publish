---
id: hvd8818q6qo5xxfok5lhye7
title: Delta Live Tables
desc: ''
updated: 1669728364246
created: 1669724994686
---

## Streaming data processing

### Python
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

### SQL
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

- Data source > Bronze
    - A job that ingests raw data from a streaming source into the Lakehouse
- Bronze > Silver
    - A job that enriches data by parsing its timestamps into a human-readable format
- Silver > Gold
    - A job that queries aggregated data to publish key insights into a dashboard
    - A job that develops a feature set for a machine learning application
    - A job that aggregates cleaned data to create standard summary statistics




    

