---
id: t9h5i24qpl5wpfziw749zvv
title: Spark Config
desc: ''
updated: 1669883845633
created: 1669414963248
---

## 파티션 수

`spark.sql.shuffle.partitions`: 셔플이 끝난 후의 RDD 파티션 수 (default: 200)

`spark.sql.autoBroadcastJoinThreshold`: broatcast() 연산을 사용하지 않고도 브로드캐스팅을 설정 (default: 10MB)


## References
- 아파치 스파크 입문, p188