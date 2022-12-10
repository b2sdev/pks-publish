---
id: cmfutyhgtl88lr1sike6zta
title: Structured Streaming
desc: ''
updated: 1670590991623
created: 1669722226613
---

## What

- Structured stream에서 data stream은 계속해서 append되는 테이를로 간주됨

![](https://learn.microsoft.com/en-us/azure/databricks/_static/images/getting-started/gsasg-spark-streaming-workflow.png)

## Why

- 이렇게 하면 stream processing model을 batch processing model처럼 처리할 수 있음

![](https://learn.microsoft.com/en-us/azure/databricks/_static/images/getting-started/gsasg-spark-streaming-model.png)

- 시간이 지날수록 새로운 row가 입력 테이블에 append되는 꼴이 되며 (Input), 이 테이블을 query하면 (Query), 결과 테이블도 계속 업데이트됨 (Output)

## How

### Initialize the stream
```python
streamingInputDF = (
  spark
    .readStream
    .schema(jsonSchema)
    .option("maxFilesPerTrigger", 1)
    .format("json")
    .load(inputPath)
)

streamCountsDF = (
  streamingInputDF
    .groupBy(
      streamingInputDF.action,
      window(streamingInputDF.time, "1 hour"))
    .count()
)
```

### Start the streaming job
```python
query = (
  streamingCountsDF
    .writeStream
    .format("memory")
    .queryName("counts")
    .outputMode("complete")
    .start()
)
```

## Reference
- https://learn.microsoft.com/en-us/azure/databricks/getting-started/streaming