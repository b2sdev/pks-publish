
## What

- Structured stream에서 data stream은 계속해서 append되는 테이블로 간주됨

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

## Trigger

### 시간 기반 트리거 간격 지정
- Structured Streaming의 시간 기반 trigger는 기본적으로 500ms의 고정 간격 micro-batches
- `processTime` 키워드를 사용하여 기간(예: `.trigger(processingTime='10 seconds'))`을 문자열로 지정

## 증분 일괄 처리 구성
- 원본 디렉터리의 모든 새 데이터를 단일 micro-batch로 처리하려면 `.trigger(once=True)` 옵션을 사용
- 스트리밍 입력 크기가 큰 경우 `.trigger(availableNow=True)` 옵션 사용

## Reference
- https://learn.microsoft.com/en-us/azure/databricks/getting-started/streaming
- https://learn.microsoft.com/en-us/azure/databricks/structured-streaming/triggers