---
id: 9le0nqs1qq4ep2dzy27dorn
title: ETL vs ELT
desc: ''
updated: 1693813712156
created: 1693812817978
---

## Summary
ETL은 데이터 변환의 복잡성을 처리하기 위해 중앙에서 데이터를 변환하는 반면, ELT는 데이터 웨어하우스의 스케일 및 처리 능력을 활용하여 변환을 수행

## ETL (Extract, Transform, Load)

### What
- 데이터를 원본 소스에서 추출하고, 변환 프로세스를 거쳐 원하는 방식으로 만든 후, 목표 데이터 웨어하우스에 로드하는 과정

### Why
- 미리 변환된 데이터를 데이터 웨어하우스에 로드하기 때문에, 일단 데이터가 로드되면 쿼리 성능이 빠름
- 원본 데이터의 품질이나 일관성에 문제가 있을 경우, 변환 단계에서 해당 문제를 해결할 수 있음
- 전통적인 관계형 데이터베이스 시스템에 잘 맞음

### When
- 구조화된 데이터를 가진 전통적인 데이터 웨어하우스 환경에서의 데이터 처리와 통합

## ELT (Extract, Load, Transform)

### What
- 데이터를 원본 소스에서 추출한 후, 먼저 목표 데이터 웨어하우스에 로드하고, 데이터 웨어하우스 내에서 필요한 변환 작업을 수행하는 과정

### Why
- 현대의 데이터 웨어하우스 솔루션은 대용량의 데이터 변환 작업을 빠르게 처리할 수 있으므로 ELT가 가능
- 데이터 로딩 후 변환을 수행하기 때문에, 다양한 형식의 데이터를 빠르게 데이터 웨어하우스에 가져올 수 있음
- 데이터 웨어하우스에서 직접 변환을 수행하기 때문에, 변환 로직을 쉽게 변경하거나 업데이트할 수 있음

### When
- 빅데이터 및 클라우드 기반 데이터 웨어하우스 환경 또는 데이터 웨어하우스 내에서 다양한 형식의 데이터를 동적으로 변환 및 집계해야 할 때