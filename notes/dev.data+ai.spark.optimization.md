---
id: n5zbm8d7522ndfjfsreix5s
title: Spark 분산 처리 최적화
desc: ''
updated: 1693660316922
created: 1693658941862
---

## 1. Partitioning (파티셔닝)

- Spark는 데이터를 파티션별로 나눠 처리함. 적절한 파티션 크기와 수를 선택함으로써, 효율적인 데이터 처리와 리소스 사용이 가능함.
- `repartition()` 및 `coalesce()` 함수를 사용하여 데이터 파티션 수를 조절할 수 있음.

## 2. Persisting (데이터 지속성)

- 자주 사용하는 RDD나 DataFrame은 메모리에 캐시하거나 디스크에 저장하여 재계산 없이 빠르게 액세스 할 수 있도록 함.
- `persist()` 또는 `cache()` 메서드를 사용하여 선택적으로 저장 수준을 지정할 수 있음.

## 3. Broadcasting (브로드캐스팅)

- 큰 DataFrame과 작은 DataFrame을 조인할 때, 작은 DataFrame을 모든 노드에 복사하여 네트워크 트래픽을 최소화 할 수 있음.

## 4. Avoiding Shuffling (셔플링 피하기)

- 셔플링은 클러스터 전체의 데이터 재분배를 의미하며, 비용이 많이 듦. 가능한한 셔플링을 최소화하는 연산을 선택하거나, 셔플링이 필요한 연산을 최적화함.

## 5. Tuning Spark Configurations (Spark 설정 튜닝)

- Spark의 설정 옵션은 작업의 특성에 따라 조정될 수 있음
- 예를 들면, `spark.executor.memory`나 `spark.driver.memory`와 같은 설정을 통해 자원 할당량을 조절할수 있음.

## 6. Using DataFrames over RDDs

- DataFrame은 Catalyst 옵티마이저를 활용화여 연산을 최적화함.
- 가능하면 RDD 대신 DataFrame API를 사용하는 것이 좋음.

## 7. Monitoring and Profiling (모니터링 및 프로파일링)

- Spark UI는 실행 중인 작업의 성능과 병목 현상을 모니터링하는데 유용함. 이를 통해 잠재적인 문제를 발견하고 최적화 할 수 있음.