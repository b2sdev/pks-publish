---
id: i77f7bz5g58kgrwmzz5rf07
title: ACID 트랜잭션
desc: ''
updated: 1670590832894
created: 1669900984075
---

## Transaction
  - 데이터베이스에서 데이터에 대한 하나의 논리적 실행 단계<br>
    ㄴ 예) 은행에서의 계좌 이체 : 계좌 이체의 구현은 내부적으로 여러 단계로 이루어질 수 있지만 전체적으로는 '송신자 계좌의 금액 감소'와 '수신자 계좌의 금액 증가'가 한 동작으로 이루어져야 함

## ACID
  - `Atomicity` (원자성)<br>
    : transaction과 관련된 작업들이 부분적으로 실행되다가 중단되지 않는 것을 보장하는 능력
  - `Consistency` (일관성)<br>
    : transaction이 실행을 성공적으로 완료하면 언제나 일관성 있는 데이터베이스 상태로 유지하는 것
  - `Isolation` (독립성)<br>
    : transaction을 수행 시 다른 transaction의 연산 작업이 끼어들지 않도록 보장하는 것
  - `Durability` (지속성)<br>
    : 성공적으로 수행된 transaction은 영원히 반영되어야 함
  
cf)
  - ACID stands for atomicity, consistency, isolation, and durability.
  - `Atomicity` means that all transactions either succeed or fail completely.
  - `Consistency` guarantees relate to how a given state of the data is observed by simultaneous operations.
  - `Isolation` refers to how simultaneous operations potentially conflict with one another.
  - `Durability` means that committed changes are permanent.

## Reference
- https://ko.wikipedia.org/wiki/ACID
- https://docs.databricks.com/lakehouse/acid.html