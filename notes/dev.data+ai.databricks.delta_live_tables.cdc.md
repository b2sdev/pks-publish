---
id: yafhr4wma720uky7t582yzq
title: Change Data Capture with Delta Live Tables
desc: ''
updated: 1670636051256
created: 1669885785274
---

## What
- 원본 데이터가 변경되면 Delta Live Table pipeline이 실행되어 table이 자동으로 업데이트되게 하는 것

## How
- `APPLY CHANGES INTO` query 또는 `apply_changes` function 실행

## Reference
- https://docs.databricks.com/workflows/delta-live-tables/delta-live-tables-cdc.html