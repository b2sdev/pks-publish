---
id: amhbge9cv2vmha17e12isfu
title: Spark Overview
desc: ''
updated: 1669212339663
created: 1669210433558
---


- RDD
    - 변경할 수 없는 형태의 분산된 객체들의 모음
    - executor 또는 worker node에 저장됨
    - RDD를 구성하는 객체를 `partition`이라 함

- 스파크 클러스터 매니저
    - 스파크 애플리케이션에서 설정한 parameter에 따라 분산 시스템에 executor들을 실행하고 분산해 주는 역할

- 스파크 실행 엔진
    - 연산을 위해 executor들에게 데이터를 분산해 주고 실행을 요청

- 지연 평가
    - 스파크 애플리케이션은 드라이버 프로그램이 action을 호출하기 전까지는 '아무것도' 하지 않음

- Transformation
    - transformation은 자신에게 의존하는 action이 호출되기 전까지는 실행되지 않음
    - wide transformation : shuffle이 수반됨
    - narrow transformation : shuffle이 발생하지 않음

- Action
    - 스파크 RDD에 분산된 데이터를 RDD 밖으로 꺼내는 행위
        - 예: 데이터를 드라이버에 되돌려 주거나 저장 시스템에 저장
    - action은 DAG에서 leaf 노드 형태가 됨
    - 스파크 스케줄러는 각 action마다 실행 그래프를 만들고 스파크 잡을 시작 

- Job
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

## References
- High Performance Spark