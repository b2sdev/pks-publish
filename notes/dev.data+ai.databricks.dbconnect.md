---
id: 1ncwv3zac3km8grtf7etpta
title: Databricks Connect
desc: ''
updated: 1669277557353
created: 1669277202846
---


- Databricks Connect의 구문 분석 및 계획 작업은 로컬 컴퓨터에서 실행되는 반면, 작업은 원격 컴퓨팅 리소스에서 실행됨 --> 런타임 오류를 디버그하기 힘듦


- 로컬 컴퓨터의 파일을 (원격 클러스터에서) 처리하고 싶은 경우
    1. Pandas로 로컬 컴퓨터의 파일을 읽는다.
    2. Pandas dataframe을 Spark dataframe으로 변환한다.
    3. ...
    4. 결과를 로컬 컴퓨터에 저장하려면 Spark dataframe을 Pandas dataframe으로 변환 후 저장한다.
```python
import pandas as pd
from pyspark.sql import SparkSession

spark = SparkSession.builder.getOrCreate()

df = spark.createDataFrame(pd.read_csv('./data/sample.csv'))

df.toPandas().to_parquet('./data/result.parquet')
```