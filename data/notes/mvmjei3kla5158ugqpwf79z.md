
## 중요 정보
- 스파크는 병렬 분산 환경을 의식하지 않고 처리를 기술할 수 있는 것을 목표로 한다.


## Terms
term|description
---|---
RDD|Resilient Distributed Dataset, 내결함성 분산 데이터셋


## Spark Session
```python
spark = SparkSession.builder().getOrCreate()
```


## UDF
```python
@udf
def extract(x):
    # do something

extract = udf(functools.partial, extract, 'key')
```

## 브로드캐스트 변수
- 복수의 executor가 공통으로 참조하는 데이터는 *브로드캐스트 변수*로 배포

## Dataframe Source
- https://github.com/apache/spark/blob/master/python/pyspark/sql/dataframe.py

## Reference
- 아파치 스파크 입문
- https://github.com/spark-in-action/first-edition