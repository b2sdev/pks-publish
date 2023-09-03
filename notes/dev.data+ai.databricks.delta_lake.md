---
id: f5ta5qp6kvcp8x23oxfjwi2
title: Delta Lake
desc: ''
updated: 1693717299550
created: 1669726561783
---

## What
- an open source ACID table storage layer over cloud object stores
- parquet 데이터 파일을 확장<br>
    ㄴ How? transaction log를 추가하여 <br>
    ㄴ So? [[dev.cs.database.ACID]]을 제공하고, 확장 가능한 메타데이터를 처리
- Apache Spark API 와 완벽하게 호환되며 [[dev.data+ai.spark.structured_streaming]]과의 긴밀하게 통합됨
<br>
    ㄴ So? 일괄 처리 및 스트리밍 작업 모두에 단일 데이터 복사본을 쉽게 사용하고, 대규모 증분 처리를 제공할 수 있음
- Databricks의 [[dev.data+ai.databricks.data_lakehouse]] 플랫폼에서는 데이터 및 테이블을 저장하기 위한 기반을 제공하는 최적화된 `스토리지 계층`으로 사용됨

> Delta Lake is an open source ACID table storage layer over cloud object stores initially
developed at Databricks. Delta Lake uses a transaction log that is
compacted into Apache Parquet format to provide ACID properties,
time travel, and significantly faster metadata operations for large
tabular datasets (e.g., the ability to quickly search billions of table
partitions for those relevant to a query). It also leverages this design to provide high-level features such as automatic data layout
optimization, upserts, caching, and audit logs.

## WHY
- [[dev.data+ai.data_lake]]는 Schema Enforcement, Data Quality, ACID Transaction 등을 지원하지 않음
- 이러한 Data Lakes의 결점을 Delta Lake로 극복할 수 있음

## Z-ordering
- Z-ordering is a technique to colocate related information in the same set of files. This co-locality is automatically used by Delta Lake on Databricks data-skipping algorithms. This behavior dramatically reduces the amount of data that Delta Lake on Databricks needs to read. 

```sql
OPTIMIZE events
WHERE date >= current_timestamp() - INTERVAL 1 day
ZORDER BY (eventType)
```

## Reference
- https://learn.microsoft.com/en-us/azure/databricks/delta/
- https://www.databricks.com/wp-content/uploads/2020/08/p975-armbrust.pdf
- https://www.linkedin.com/pulse/delta-lake-tables-umair-yelurkar