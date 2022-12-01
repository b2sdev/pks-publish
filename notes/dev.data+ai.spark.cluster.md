---
id: l79vrhuhxtx2luc014n20sr
title: Cluster
desc: ''
updated: 1669862285624
created: 1667041491502
---

## 스파크 런타임 컴포넌트

### 클라이언트 프로세스
- 드라이버 프로그램을 시작
    > Spark 프로그램을 실행하는 방법
    1. spark-submit 명령으로 프로그램을 제출
    2. Spark shell에서 프로그램을 실행
    3. 별도의 애플리케이션에서 SparkContext 객체를 초기화 및 설정

### 드라이버의 역할

- 스파크 애플리케이션의 실행을 관장하고 모니터링 (스파크 애플리케이션을 감싸는 일종의 래퍼 역할)
    - 클러스터 매니저에 메모리 및 CPU 리소스를 요청
    - 애플리케이션 로직을 stage와 task로 분할
    - 여러 executor에 task를 전달
    - task 실행 결과를 수집

- 드라이버 프로그램 배포 모드
    - 클라이언트 모드
        - 드라이버를 클라이언트의 JVM 프로세스에서 실행
        
            ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FOZH7c%2FbtqYhydgOoQ%2FGZkzj48MpqcrdutMdnDAL0%2Fimg.png)
    - 클러스터 모드
        - 드라이버 프로세스를 클러스터 내부에서 별도의 JVM 프로세스로 실행하며, 드라이버 프로세스의 리소스(주로 JVM 힙 메모리)를 클러스터가 관리
        > When Spark runs in Cluster Mode, the Spark Driver runs in a worker node inside the cluster. In <b>Cluster Mode</b>, the cluster manager launches the driver process on a worker node inside the cluster, in addition to the executor processes. This means that the cluster manager is responsible for maintaining all Spark worker nodes. Therefore, the cluster manager places the driver on a worker node and the executors on separate worker nodes.
        
        ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbIPFml%2FbtqX32tKwYS%2FU6KUycWZRuw1pKkkRgRMa0%2Fimg.png)
    - 로컬 모드
        - spark-submit 명령을 실행한 후 클라이언트 상에서 프로세스를 구동하고, 해당 프로세스 안에서 executor를 구동하여 애플리케이션을 실행하는 동작 모드
            - `spark-submit --master local` # 1개의 executor와 1개의 core로 실행
            - `spark-submit --master local[N]` # 1개의 executor와 N개의 core로 실행
            - `spark-submit --master local[*]` # 1개의 executor와 로컬 머신이 갖고 있는 만큼의 core로 실행
        
        ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcU9nst%2FbtqX1pW1SsP%2FxRPXLbjhYuTXG6aqGiomb0%2Fimg.png)


### Executor의 역할
- Executor는 드라이버가 요청한 task들을 받아서 실행하고, 그 결과를 드라이버로 반환하는 JVM 프로세스
- 각 executor는 드라이버가 요청한 tasks들을 여러 task slot에서 병렬로 실행
    - 일반적으로 task slop 개수는 CPU 코어 개수의 두세 배 정도로 설정

### SparkContext의 생성
- 드라이버는 SparkContext 인스턴스를 생성하고 시작
    - SparkContex는 RDD를 생성하거나 데이터를 로드하는 등 다양한 작업을 수행하는 여러 유용한 메서드를 제공하며, 스파크의 런타임 인스턴스에 접근할 수 있는 기본 인터페이스


## 주요 Configuration

### Application configuration

configuration|description
---|---
spark.driver.cores  |   드라이버가 사용할 코어 수. 클러스터 모드에서만 유효하며 기본값은 1
spark.driver.maxResultSize  |   collect() 결과로 생성된 결과 값의 최대 크기. 이 값 초과 시 전체 job은 실패로 종료됨. 기본값은 1g
spark.executor.memory   |   executor 하나의 메모리 크기. 기본값 1g

### Executor configuration

configuration   | description
---|---
spark.executor.cores    |   executor에 할당할 코어 수 지정

## Configuration 등록 방법

1. Spark 스크립트로 SparkSession 생성 시 지정
2. spark shell이나 spark-submit에서 명령행 매개변수로 지정
3. spark-defaults.conf로 지정

## References
- 스파크를 다루는 기술 (Spark in Action)
- https://m.blog.naver.com/occidere/221609076332