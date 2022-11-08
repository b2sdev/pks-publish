---
id: sfeu6c5r2tcv2mgr2xpo696
title: Dataframe
desc: ''
updated: 1667042550960
created: 1667042550960
---

## Dataframe 생성

```python
df = spark.createDataFrame([
  ('01', 'aws'),
  ('02', 'azure'),
  ('03', 'gcp')
], ())
df.show()
```

## 데이터 읽기
```python
df = spark.read.parquet("path/to/x.parquet")
```

## 데이터 저장
```python
# 하나의 파일로 저장
df.coalease(1).write.format().mode('overwrite').option('header', 'true').save(path)
```

## 컬럼 조작
What|How
---|---|---
선택    |   df.select('id', 'body')
제거	|   df.drop('body')
필터링	|   df.filter(() and ()).limit(10)
추가	|   df.withColumn('col', lit(1))
이름 변경	|   df.withColumnRenamed('ownerUserId', 'owner')
정렬	|   df.orderBy() <br> df.sort()
조건	|   when((f.col('a').cast(IntegerType()) > 0), 1).otherwise(0)
이름 변경	|   col_name = [...] <br> df.toDF(*col_name)

## 데이터 처리
What|How
----|---
필터	|df.filter
정렬	|df.orderBy()
집약	|df.agg(avg(col("kcal")) as "") <br> df.groupBy(...).agg(max(~).alias(~))
결합	|df.join(df2, on=[...], how="inner/left") <br> df.join(df2, df['id'] == postId, 'outer')
집계	| df.groupBy().agg… <br> df.distinct()


## SQL 활용
```python
df.registerTempTable("dessert_table")
df.createOrReplaceTempView("dessert_table")
numOver300KcalDf = spark.sql("SELECT cound(*) AS num_of_over_30Kcal FROM dessert_table WHERE kcal >= 260")
```
