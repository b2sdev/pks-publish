---
id: fu8wshgb2pwe2pm3rthbjva
title: OLTP vs OLAP
desc: ''
updated: 1693729581047
created: 1668458676678
---

## OLTP (Online Transactional Processing; 온라인 트랜잭션 처리)
- **트랜잭션 중심**의 데이터 처리 시스템을 일컫는 용어<br>
    ㄴ 데이터베이스의 데이터를 수시로 갱신하는 프로세싱<br>
    ㄴ 호스트 컴퓨터가 데이터베이스를 액세스하고, 바로 처리 결과를 돌려주는 형태
- 빠르고 효율적인 쿼리와 정확한 최신 정보를 필요로 하는 경우에 적합
- 행 기반
- 기존 DBMS
- Amazon RDS

## OLAP (Online Analytical Processing; 온라인 분석 처리)
- 성능 및 일상적인 사용보다는 데이터 분석 및 의사 결정에 초점을 맞춘 데이터 처리 시스템을 일컫는 용어<br>
    ㄴ 대용량 데이터 집합을 대상
- 보통은 비즈니스 인텔리전스(BI) 솔루션과 연동
- 컬럼 기반
- Amazon Redshift

## Summary

| **구분**        | **OLTP**                                | **OLAP**         |
|---------------|-----------------------------------------|------------------|
| **기초**        | 많은 수의 온라인 단기거래 관리                       | 데이터 분석에 사용       |
| **데이터베이스 타입** | 기존 DBMS 사용                              | 데이터 웨어하우스(DW) 사용 |
| **데이터 수정**    | 모든 insert, update, delete transaction 관리 | 데이터 읽기에 사용       |
| **응답시간**      | 밀리초 단위                                  | 처리가 조금 느림        |
| **정규화**       | 정규화 O                                   | 정규화 X            |
| **데이터 특성**    | 트랜잭션 중심                                 | 주제 중심            |


## Reference
- https://simroot.tistory.com/24