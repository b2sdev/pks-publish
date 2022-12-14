---
id: hrfn1n5bbgtgr2tezf49j0k
title: OpenSearch
desc: ''
updated: 1669271151851
created: 1669270246176
---

- `OpenSearch`는 커뮤니티 주도의 검색 및 분석 오픈소스이며, 엘라스틱서치 7.10.2 버전에서 분기됨
- `OpenSearch`는 Apache Lucene 기반의 분선 검색 엔진이며, `OpenSearch Dashboards`는 데이터 시각화 및 유저인터페이스를 제공
- 엘라스틱서치 오픈 배포판의 모든 기능을 포함

## OpenSearch 용어

클러스터/도메인|노드로 분산 구성된 시스템
---|---
노드|컴퓨팅 자원과 스토리지를 가진 개별 인스턴스를 의미. 리더노드와 데이터 노드가 있음.
인덱스|도큐먼트를 저장하는 논리적 구분자로서 하나 이상의 샤드로 구성.
샤드|여러 대 노드를 효율적으로 사용하기 위해 도큐먼트를 샤드라는 단위로 나눠 분산 저장. 성능과 처리량을 높이며, 프라이머리 샤드와 레플리카 샤드가 있음.
도큐먼트|데이터가 저장되는 기본 단위. JSON 구조로 여러 필드와 값을 가짐.

## 관계형 DB와 OpenSearch 비교

관계형DB|OpenSearch
---|---
테이블|인덱스
레코드|도큐먼트
컬럼|필드
스키마|매핑

- 인덱스는 샤드들로 구성됨
- 다수 노드에 샤드가 분산 저장되며 수평 확장 가능
 
## References
- AWS Builders Korea Program 200 : Amazon OpenSearch Service로 실시간 데이터 분석과 시각화 기본기 다지기