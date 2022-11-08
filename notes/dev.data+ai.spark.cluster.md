---
id: l79vrhuhxtx2luc014n20sr
title: Cluster
desc: ''
updated: 1667041491502
created: 1667041491502
---

## 주요 Configuration

### Application configuration

configuration|description
---|---
spark.driver.cores  |   드라이버가 사용할 코어 수. 클러스터 모드에서만 유효하며 기본값은 1
spark.driver.maxResultSize  |   collect() 결과로 생성된 결과 값의 최대 크기. 이 값 초과 시 전체 job은 실패로 종료됨. 기본값은 1g
spark.executor.memory   |   익스큐터 하나의 메모리. 기본값 1g

### Executor configuration

configuration   | description
---|---
spark.executor.cores    |   익스큐터에 할당할 코어 수 지정

## Configuration 등록 방법

1. Spark 스크립트로 SparkSession 생성 시 지정
2. spark shell이나 spark-submit에서 명령행 매개변수로 지정
3. spark-defaults.conf로 지정

### References
- https://m.blog.naver.com/occidere/221609076332