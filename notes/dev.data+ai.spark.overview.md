---
id: amhbge9cv2vmha17e12isfu
title: Spark Overview
desc: ''
updated: 1669432220730
created: 1669210433558
---


### RDD
- RDD
    - 분산 컬렉션 자료구조로 대량의 데이터를 요소(element)로 가짐
        - 여러 머신으로 구성된 클러스터 환경에서 분산 처리를 전제로 설계됨
    - 내부는 `partition`이라는 단위로 나뉨
        - partition
            - RDD를 구성하는 객체
            - 스파크에서는 이 파티션이 분산 처리 단위
            - RDD를 파티션 단위로 독립해 여러 머신에서 분산 처리
    - 변경할 수 없는 형태의 분산된 객체들의 모음
    - executor 또는 worker node에 저장됨

- RDD 처리
    - transformation(변환)
        - RDD를 가공하고 그 결과로 새로운 RDD를 얻는 처리
        - shuffle(셔풀)
            - 서로 다른 파티션에 있는 같은 키를 가지는 요소의 자리를 바꾸는 것
            - executor 간의 다대다 네트워크 통신이 필요해짐 ~ 부하가 높은 처리
        - narrow transformation : shuffle이 발생하지 않음
            - 하나의 `stage` 안에서의 연산
        - wide transformation : shuffle이 수반됨
            - 각 partition에서 계산해야 하는 데이터들이 여러 머신에 나누어져 있기 때문에
            - shuffle이 완료된 후에 이후 연산이 시작됨
            - `정렬`은 단순히 각 파티션에서만 정렬되는 것이 아니라 모든 레코드들이 정의된 순서에 따라 정렬되어 있어야 하므로 narrow transformation으로는 해결할 수 없음
            
            ![](https://images.squarespace-cdn.com/content/v1/5bce4071ab1a620db382773e/dbbdd8e6-5f2a-45f5-a232-825dca3fa816/Narrow+Transformation.png?format=500w) | ![](https://images.squarespace-cdn.com/content/v1/5bce4071ab1a620db382773e/282af54b-d7d1-427e-b602-fdb3effc59a4/Wide+Transformation.png?format=500w)
            ---|---
            Narrow Transformation|Wide Transformation
            filter()<br>contains()<br>|orderBy()<br>repartition()
        - transformation은 자신에게 의존하는 action이 호출되기 전까지는 실행되지 않음
    - action(액션)
        - RDD 내용을 바탕으로 더이상 데이터를 가공하지 않고 원하는 결과를 얻는 조작
        - 스파크 RDD에 분산된 데이터를 RDD 밖으로 꺼내는 행위
            - 예: 데이터를 드라이버에 되돌려 주거나 저장 시스템에 저장
        - action은 DAG에서 leaf 노드 형태가 됨
        - 스파크 스케줄러는 각 action마다 실행 그래프를 만들고 스파크 잡을 시작 

- 스파크 클러스터 매니저
    - 스파크 애플리케이션에서 설정한 parameter에 따라 분산 시스템에 executor들을 실행하고 분산해 주는 역할
    - Executors are launched by the cluster manager on behalf of the driver.

- 스파크 실행 엔진
    - 연산을 위해 executor들에게 데이터를 분산해 주고 실행을 요청

- 지연 평가
    - 스파크 애플리케이션은 드라이버 프로그램이 action을 호출하기 전까지는 '아무것도' 하지 않음

- Job
    - 스파크 애플리케이션에서는 RDD 생성부터 액셔 적용까지를 통틀어 job이라는 단위로 처리
    - 스파크 job은 하나의 최종 결과를 연산해 내는 데 필요한 RDD transformation들의 집합
    - 각 job은 최종 RDD를 만들어 내는 데 필요한 데이터 변환(transformation)의 각 단계를 의미하는 stage들로 구성됨

- Stage
    - job의 일부분으로 하나의 executor에서 계산 가능한 task들의 집합
    - 하나의 stage는 partition들끼리 데이터가 전송되는 일 없이 병렬로 연산이 가능한 단위
    - shuffle이 발생할 때 시작됨

- Task
    - 한 stage 안에서 데이터의 각 partition에 대한 작업을 수행하는 단위

![](/assets/images/spark_application.png)
    - 분산 시스템에서 스파크 애플리케이션 시작하기

![](https://images.squarespace-cdn.com/content/v1/5bce4071ab1a620db382773e/57966b9e-d905-4bb0-95c8-d2ca5def572d/Spark+Execution+Hierarchy.png?format=2500w)
    - Job - Stage - Task

- RDD 영속화(persistent)
    - executor는 task 처리를 끝낼 때, 처리 과정에서 생성된 partition 인스턴스를 영속화하는 경우가 있음
    - Case#1 : 셔플이 발생하는 transformation을 실행하기 직전의 RDD
    - Case#2 : 사용자에 의해서 명시적으로 영속화가 선언된 RDD


- Broadcast variables
    - Broadcast variables are shared, immutable variables that are cached on every machine in the cluster instead of serialized with every single task

## References
- 하이 퍼포먼스 스파크
- 아파치 스파크 입문
- https://www.advancinganalytics.co.uk/blog/2022/6/8/tips-for-the-databricks-certified-associate-developer-for-apache-spark-30