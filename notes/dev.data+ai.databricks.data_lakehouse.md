---
id: 2b76tsb8q0aqabl8uww9at1
title: Data Lakehouse
desc: ''
updated: 1669729185371
created: 1669725901082
---

## Data lakehouse의 장점
- A data lakehouse enables both batch and streaming analytrics.
- A data lakehouse stores unstructured data and is ACID-compliant.

## Incremental Multi-Hop in the Lakehouse

![](/assets/images/databricks-multi-hop.png)

파이프라인의 각 Bronze,Silver,Gold 데이터 단계별로 프로세싱되는 과정을 거치면서 가장 최신의 데이터를 준실시간성(near-real time)으로 처리하여 분석가에게 제공됨

- Bronze 테이블은 다양한 소스((JSON files, RDBMS data, IoT data등)에서 수집한 원본 데이터를 저장
- Silver 테이블은 우리 데이터에 좀더 정제된 view를 제공합니다. 다양한 bronze 테이블과 조인하거나 불필요한 정보의 제거, 업데이트등을 수행
- Gold 테이블은 주로 리포트나 대시보드에서 사용되는 비지니스 수준의 aggregation을 수행한 뷰를 제공 (예: 일간 사용자수나 상품별 매출 등의 뷰)