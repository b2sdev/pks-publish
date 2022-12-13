---
id: jgxvkvj6ety2k8jdh6ia3un
title: Expectations
desc: ''
updated: 1670641866298
created: 1670636250667
---

## What
[[dev.data+ai.databricks.delta_live_tables]]에서는 -데이터셋의 컨텐츠에 대해- 데이터 품질 제약조건([[dev.data+ai.data_ingestion.constraint]])을 지정하여 데이터 유효성(expectation)을 확보할 수 있음

## How
**Expectation** | **기대 동작**
----------------|------------
expect_all | 유효성 검사에 실패한 레코드가 데이터 세트에 포함
expect_all_or_drop | 유효성 검사에 실패한 레코드를 데이터 셋트에서 삭제
expect_all_or_fail | 유효성 검사에 실패한 레코드가 있으면 파이프라인 실행을 중지

### Python

```python
@dlt.expect("valid timestamp", "col(“timestamp”) > '2012-01-01'")
@dlt.expect_or_drop("valid_current_page", "current_page_id IS NOT NULL AND current_page_title IS NOT NULL")
@dlt.expect_or_fail("valid_count", "count > 0")
```

### SQL
```SQL
CONSTRAINT valid_timestamp EXPECT (timestamp > '2012-01-01')
CONSTRAINT valid_current_page EXPECT (current_page_id IS NOT NULL and current_page_title IS NOT NULL) ON VIOLATION DROP ROW
CONSTRAINT valid_count EXPECT (count > 0) ON VIOLATION FAIL UPDATE
```

## Reference
- https://docs.databricks.com/workflows/delta-live-tables/delta-live-tables-expectations.html