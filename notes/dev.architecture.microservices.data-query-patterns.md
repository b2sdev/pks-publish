---
id: rc5ks6o8knqqwbdlubjye6d
title: Data Query Patterns
desc: ''
updated: 1693656429946
created: 1692968541450
---

## Question
모놀리식 애플리케이션은 전체 데이터가 하나의 DB에 있기 때문에 SELECT 문으로 여러 테이블을 조인하는 쿼리를 작성할 수 있습니다. 마이크로서비스는 각 서비스마다 각자 DB를 갖는데 각 서비스가 소유한 데이터를 조인하는 쿼리를 어떻게 구현할 수 있을까요?

## Answer
마이크로서비스 아키텍처에서는 다음 두 가지 패턴으로 쿼리를 구현합니다.
- API 조합(composition) 패턴: 서비스 클라이언트가 데이터를 가진 여러 서비스를 직접 호출하여 그 결과를 조합하는 패턴입니다.
- CQRS(Command Query Responsibility Segregation, 커맨드 쿼리 책임 분산) 패턴: 쿼리만 지원하는 하나 이상의 뷰(view) 전용 데이터 레플리카(replica, 사본/복제본)를 유지하는 패턴입니다.

### API 조합 패턴
#### What
여러 서비스에 있는 데이터를 API를 통해 조회하고 그 결과를 조합하여 쿼리를 구현합니다.

<div style="text-align:center"><img src="https://microservices.io/i/data/ApiBasedQueryBigPicture.png" /></div>

#### HOW
데이터를 조합하는 API 조합기는 세 가지 옵션이 있습니다.

첫째, 웹 애플리케이션처럼 웹 페이지에 데이터를 렌더링하는 서비스 클라이언트를 API 조합기로 임명하는 것입니다.

둘째, 애플리케이션의 외부 API가 구현된 API 게이트웨이를 API 조합기로 만드는 것입니다.

셋째, API 조합기를 스탠드얼론 서비스로 구현하는 것입니다.

### CQRS 패턴
#### What
여러 서비스에 있는 데이터를 가져오는 쿼리는 (이벤트를 이용하여) 해당 서비스의 데이터를 복제한 읽기 전용 뷰를 유지합니다.

<div style="text-align:center"><img src="https://miro.medium.com/v2/resize:fit:3712/1*KtVJ1SVJSQWE9DOafLU8bw.png"></div><br>

이 패턴은 영속적 데이터 모델과 그것을 사용하는 모듈을 커맨드와 쿼리, 두 편으로 가릅니다. 조회(R) 기능(예: HTTP GET)은 쿼리 쪽 모듈 및 데이터 모델에, 생성/수정/삭제(CUD) 기능(예: HTTP POST, PUT, DELETE)은 커맨드 쪽 모듈 및 데이터 모델에 구현하는 것입니다. 양쪽 데이터 모델 사이의 동기화는 커맨드 쪽에서 발행한 이벤트를 쿼리 쪽에서 구독하는 식으로 이루어집니다.

<div style="text-align:center"><img src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*60XHay_uTUyV-hwDJBTIug.png">이미지 출처: https://medium.com/the-legend/cqrs-81b2de39dfd5</div>

### 패턴 선택
API 조합 패턴을 이용하면 여러 서비스에 있는 데이터를 조회하는 쿼리를 쉽게 구현할 수 있습니다. 가급적 이 방법을 쓰는 것이 좋습니다.
그러나, API 조합 패턴만으로는 효율적으로 구현하기 어려운 (가령 거대한 데이터 뭉치를 인-메모리 조인하는) 다중 서비스 쿼리인 경우 CQRS 패턴을 사용하는 것이 바람직합니다. CQRS 패턴은 API 조합 패턴보다 강력한 만큼 구현하기는 더 복잡합니다.

## Reference
- 크리스 리처드슨, <마이크로서비스 패턴>, 길벗