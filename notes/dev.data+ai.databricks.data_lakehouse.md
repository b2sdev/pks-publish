---
id: 2b76tsb8q0aqabl8uww9at1
title: Data Lakehouse
desc: ''
updated: 1669901272287
created: 1669725901082
---

## What

- In short, a Data Lakehouse is an architecture that enables efficient and secure Artificial Intelligence (AI) and Business Intelligence (BI) directly on vast amounts of data stored in Data Lakes.
- The Data Lakehouse enables storing all your data once in a [[dev.data+ai.data_lake]] and doing AI and BI on that data directly. 

> We define a [Lakehouse](https://www.cidrdb.org/cidr2021/papers/cidr2021_paper17.pdf?utm_source=microsoft&utm_medium=web&utm_campaign=7013f000000Tx4QAAS) as a data management system based on lowcost and directly-accessible storage that also provides traditional analytical DBMS management and performance features such as ACID transactions, data versioning, auditing, indexing, caching, and query optimization. Lakehouses thus combine the key benefits of data lakes and data warehouses: low-cost storage in an open format accessible by a variety of systems from the former, and powerful management and optimization features from the latter. - Michael Armbrust, Ali Ghodsi, Reynold Xin, Matei Zaharia

![](https://www.databricks.com/wp-content/uploads/2020/01/data-lakehouse-new.png)

- Lakehouses는 데이터 레이크의 저비용 및 유연성과 데이터 웨어하우스의 안정성 및 성능을 결합
- Lakehouse 아키텍처는 다음과 같은 몇 가지 주요 기능을 제공

    - 개방형 형식의 안정적이고 확장 가능하며 저렴한 스토리지
    - [[dev.cs.database.ACID]] 트랜잭션을 사용한 ETL 및 스트림 처리
    - 쿼리 시 관리 용이성과 성능을 보장하기 위한 메타데이터, 버전 관리, 캐싱 및 인덱싱
    - 데이터 과학 및 기계 학습을 위한 선언적 DataFrame API와 함께 BI 및 보고용 SQL API

    ![](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/243936iECABC2CB42BE68E3/image-size/medium?v=v2&px=400)


- Lakehouse instead adds traditional data warehousing capabilities to existing data lakes, including ACID transactions, fine-grained data security, low-cost updates and deletes, first-class SQL support, optimized performance for SQL queries, and BI style reporting. By building on top of a data lake, the Lakehouse stores and manages all existing data in a data lake, including all varieties of data, such as text, audio and video, in addition to structured data in tables. Lakehouse also natively supports data science and machine learning use cases by providing direct access to data using open APIs and supporting various ML and Python/R libraries, such as PyTorch, Tensorflow or [[dev.data+ai.ml.xgboost]], unlike data warehouses. Thus, Lakehouse provides a single system to manage all of an enterprise’s data while supporting the range of analytics from BI and AI.

### Lakehouse의 3가지 핵심 원칙과 구성 요소
![](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/244539i02EE86FA40EC52EF/image-dimensions/671x329?v=v2)
1. 오픈 소스 형식의 선별된 레이어와 함께 모든 데이터를 저장하는 [[dev.data+ai.data_lake]]
    - 데이터 레이크는 모든 유형, 크기 및 속도의 데이터를 수용할 수 있어야 합니다. 레이크에서 선별된 데이터의 형식은 개방형이어야 하고 클라우드 네이티브 보안 서비스와 통합되어야 하며 ACID 트랜잭션을 지원해야 합니다.
2. 개방형 표준을 기반으로 구축된 기본 컴퓨팅 계층
    - 데이터 레이크 큐레이팅(ETL 및 스트림 처리), 데이터 과학 및 기계 학습, 데이터 레이크에 대한 SQL 분석을 포함한 모든 핵심 레이크하우스 사용 사례를 지원하는 기본 컴퓨팅 계층이 있어야 합니다.
3. 추가 및/또는 새로운 사용 사례를 위한 손쉬운 통합
    - 단일 서비스가 모든 것을 할 수는 없습니다. 핵심 Lakehouse 사용 사례의 일부가 아닌 새로운 또는 추가 사용 사례가 항상 있을 것입니다. 이러한 신규 또는 추가 사용 사례에는 전문 서비스나 도구가 필요한 경우가 많습니다. 이것이 바로 선별된 데이터 레이크, 기본 컴퓨팅 계층, 기타 서비스 및 도구 간의 손쉬운 통합이 핵심 요구 사항인 이유입니다.


## Data lakehouse의 장점
- A data lakehouse enables both batch and streaming analytrics.
- A data lakehouse stores unstructured data and is ACID-compliant.


## Databricks Lakehouse의 구성 요소

### [[dev.data+ai.databricks.delta_table]]

### Unity Catalog

## Incremental Multi-Hop in the Lakehouse

![](/assets/images/databricks-multi-hop.png)

파이프라인의 각 Bronze, Silver, Gold 데이터 단계별로 프로세싱되는 과정을 거치면서 가장 최신의 데이터를 준실시간성(near-real time)으로 처리하여 분석가에게 제공됨

- Bronze 테이블은 다양한 소스(JSON files, RDBMS data, IoT data등)에서 수집한 원본 데이터를 저장
- Silver 테이블은 우리 데이터에 좀더 정제된 view를 제공. 다양한 bronze 테이블과 조인하거나 불필요한 정보의 제거, 업데이트 등을 수행
- Gold 테이블은 주로 리포트나 대시보드에서 사용되는 비지니스 수준의 aggregation을 수행한 뷰를 제공 (예: 일간 사용자수나 상품별 매출 등의 뷰)

## Reference
- https://www.databricks.com/blog/2020/01/30/what-is-a-data-lakehouse.html
- https://www.databricks.com/blog/2021/08/30/frequently-asked-questions-about-the-data-lakehouse.html
- https://techcommunity.microsoft.com/t5/analytics-on-azure-blog/simplify-your-lakehouse-architecture-with-azure-databricks-delta/ba-p/2027272