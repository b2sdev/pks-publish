---
id: b8q25l0shnd5zc4ivjoaoyi
title: 클러스터 구성 최적화
desc: ''
updated: 1668242075582
created: 1668241854993
---

## Worker 노드를 하나만 사용

스파크 클러스터는 병렬 연산이 가능하고 네트워크로 연결된 머신(즉, 노드)의 집합이다. 스파크에서 데이터를 로드하면 데이터는 (row를 기준으로) 여러 파티션으로 분할되어 클러스터 노드에 고르게 분산 저장된다.

이때, groupBy로 집계를 하고 join이나 union을 통해 데이터를 통합하는 등의 작업을 수행하면, 각 파티션에 나누어 저장된 데이터는 다른 파티션으로 물리적인 이동(shuffling)을 하게 된다. 이는 네트워크 및 디스크 I/O를 야기한다.

따라서, 조인(join)이나 집계(aggregation) 등 광범위한 데이터 변환이 발생하는 셔플링(shuffling)이 빈번한 작업에는 가급적 적은 수의 노드로 클러스터를 구성하는 것이 좋다. 이와 반대로 간단한 ETL 작업(노드 사이에 데이터 이동이 발생하지 않고 각 노드의 파티션의 데이터만 사용하여 변환하는 작업)에는 연산에 최적화된 클러스터 구성을 시도해 볼 수 있다.


## References

- https://docs.microsoft.com/ko-kr/azure/databricks/clusters/cluster-config-best-practices