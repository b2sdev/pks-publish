---
id: fgo90mmygqmiichus71qo88
title: Data Warehouse
desc: ''
updated: 1670632653486
created: 1669900031102
---

## 데이터 웨어하우스
> Data warehouses are proprietary systems that are built to store and manage only structured or semi-structured (primarily JSON format) data for SQL-based analytics and business intelligence. 

- 조직 내 서로 다른 다양한 소스의 정보를 저장하고 분석할 수 있게 하는 시스템
- 대규모 데이터 저장소에 걸쳐 발생하는 복잡한 쿼리에 적합<br>
    - 예) 데이터로부터 숨겨인 인사이트를 발굴하기 위해 여러 데이터베이스에서 정보를 마이닝하는 것
    - ⭐️ 소규모의 다량의 원자성 트랜잭션에는 적합하지 않음
- 여러 다양한 데이터 저장소를 순환하는 복잡한 쿼리를 사용하므로 많은 리소스를 필요<br>
    - 확장성이 엔터프라이즈급 데이터베이스에는 미치지 못함

## 데이터베이스와의 비교
|     | **데이터베이스**    |	**데이터 웨어하우스**
  -- |-------------|----------------
주 사용 목적	| 데이터 기록	|데이터 분석
처리 방법	|OLTP	|OLAP
동시 사용자 수	|한 번에 수천 명의 사용자를 처리	|상대적으로 작은 규모의 사용자만 처리
사용 사례	|소규모의 원자성 트랜잭션에 유용	|높은 수준의 복잡한 분석
다운타임	|항시 사용 가능해야 함	|일부 예정된 다운타임 허용
최적화	|CRUD 작업 기준	|대규모 데이터 저장소에 걸쳐 발생하는 소규모의 복잡한 쿼리 기준
데이터 유형	|실시간 상세 데이터	|요약형 기록 데이터

### OLTP와 OLAP 비교
[[dev.cs.database.oltp-vs-olap]]

## 데이터 마트
- 특정 정보 유형이나 마케팅, 영업, 재무 또는 인사 등 조직 내 특정 사용자 집합을 위한 정보를 저장하는 것을 목적으로 하는 데이터베이스
- 데이터 마트는 자체 엔터티가 될 수도 있고, 대규모 데이터 웨어하우스에 속한 소규모 파티션이 될 수도 있음

## Summary
- 신속한 데이터 이용을 위해 OLTP 솔루션이 필요하면 데이터베이스를 사용
- 현재 데이터뿐만 아니라 과거 정보도 집계할 수 있는 OLAP 솔루션이 필요하면 데이터 웨어하우스 시스템 도입

## Reference
- https://www.databricks.com/blog/2021/08/30/frequently-asked-questions-about-the-data-lakehouse.html