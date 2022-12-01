---
id: f5ta5qp6kvcp8x23oxfjwi2
title: Delta Lake
desc: ''
updated: 1669900837344
created: 1669726561783
---

## What
- <b>Delta Lake</b> is an open format storage layer that delivers reliability, security, and performance.
- Enables building a [[dev.data+ai.databricks.data_lakehouse]] architecture
- <u>Parquet 데이터 파일를 확장한 것</u> w/ ACID transactions 및 확장 가능한 메타 데이터 처리를 위한 transaction log
- Apache Spark API와 완벽하게 호환되며 [[dev.data+ai.spark.structured_streaming]]과의 긴밀한 통합을 위해 개발됨

## Z-ordering
- Z-ordering is a technique to colocate related information in the same set of files. This co-locality is automatically used by Delta Lake on Databricks data-skipping algorithms. This behavior dramatically reduces the amount of data that Delta Lake on Databricks needs to read. 

```sql
OPTIMIZE events
WHERE date >= current_timestamp() - INTERVAL 1 day
ZORDER BY (eventType)
```