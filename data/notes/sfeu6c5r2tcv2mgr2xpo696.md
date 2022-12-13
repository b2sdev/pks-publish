
## Spark SQL

> Spark SQL은 옵티마이저에 의해 제어되며 사용자가 제어권을 포기

## Dataframe 생성

```python
df = spark.createDataFrame([
  ('01', 'aws'),
  ('02', 'azure'),
  ('03', 'gcp')
], ())
df.show()
```

```python
spark.createDataFrame([("summer", 4.5), ("winter", 7.5)], ["season", "wind_speed_ms"])
```

### from Python Dictionary

```python
data = [
  {'id': 10, 'name': 'Gildong', 'address': 'Seoul'},
  ...
]
df = spark.createDataFrame([data])
```

## 데이터 읽기
```python
spark.read.format("csv").option("header", True).load(filePath)
```

```python
df = spark.read.parquet("path/to/x.parquet")
```
```python
+------+-----------------------------+-------------------+
|itemId|attributes                   |supplier           |
+------+-----------------------------+-------------------+
|1     |[blue, winter, cozy]         |Sports Company Inc.|
|2     |[red, summer, fresh, cooling]|YetiX              |
|3     |[green, summer, travel]      |Sports Company Inc.|
+------+-----------------------------+-------------------+

itemsDfSchema = StructType([
  StructField("itemId", IntegerType()),
  StructField("attributes", ArrayType(StringType())),
  StructField("supplier", StringType())
])
itemsDf = spark.read.schema(itemsDfSchema).parquet(filePath)
```

```python
# return the number of columns in the CSV file stored at location filePath. From the CSV file, only lines should be read that do not start with a # character
len(spark.read.csv(filePath, comment='#').columns)
# comment – sets a single character used for skipping lines beginning with this character. By default (None), it is disabled.
```

- https://www.marks4sure.com/Databricks-Certified-Associate-Developer-for-Apache-Spark-3-0-exam.html


## 데이터 저장
```python
# 하나의 파일로 저장
df.coalease(1).write.format().mode('overwrite').option('header', 'true').save(path)
```

```python
# division으로 partitioning 후 저장
df.write.partitionBy("division").parquet(filePath)
```

```python
# 데이터 추가를 위해 저장 모드 지정
def writeAppend(input: DataFrame):
  input.write.mode("append").save("output/")
```

```python
# 우편번호로 파티션해서 저장
def writeOutByZip(input: DataFrame):
  input.write.partitionBy("zipcode").format("json").save("output/")
```

## 컬럼 조작
What|How
---|---|---
선택    |   df.select('id', 'body')
제거	|   df.drop('body') <br> df.drop('productId', 'value')
필터링	|   df.filter(col("col_1") &\| col("col_2)).limit(10)
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

## Take

```python
transactionDf.filter(col("storeId")==25).take(5)
```

## Distinct
특정 컬럼의 unique values

```python
transactionDf.select("storeId").distinct()
```

## Partition 변경

- `partitionBy`: 셔플링을 통해 새로운 RDD를 생성
- `coalesce`: 파티션 개수를 줄이거나(shuffle=false) 늘림(shuffle=true)
  - 셔플링을 피하기 위해 같은 worker 안에서 partition들을 병합
  - partition의 개수가 줄어들면서 (~병합되면서) partition 크기의 편향이 발생할 수 있음
  
  ![](https://images.squarespace-cdn.com/content/v1/5bce4071ab1a620db382773e/d14468bd-009b-4f2f-9d84-7c752862b1b8/Before+Repartition.png?format=1000w)
- `repartition`: coalesce(n, shuffle=true)와 동일
  ![](https://images.squarespace-cdn.com/content/v1/5bce4071ab1a620db382773e/4f68dd4e-fe65-4106-96c4-1060e9ab8569/After+Repartition.png?format=1000w)

## 컬럼 split

```python
from pyspark.sql.functions import split

(df.withColumn(
    "firstName", split(df["name"], " ").getItem(0)
  ).withColumn(
    "lastName", split(df["name"], " ").getItem(1)
  )
)
```

## 컬럼 이름 변경

```
df.withColumnRenamed(`old column name`, `new colun name`)
```

## 결측 값 다루기

```python
df.na.drop() # df.na.drop("any")
df.na.drop("all")
# df.na.drop(col("col_name"))
# df.na.fill(map(col("count"), 0)))

df.dropna(thresh=4) # ㅁhave missing data in a least 3 columns
```

## 첫번째 줄

```cmd
>>> df.first()
Row(age=2, name='Alice')
>>> df.first().name
Alice
```

## 조건에 따른 boolean 

```python
transactionDf.select((col("storeId").between(20, 30)) & (col("productId")==2))
```
- https://www.marks4sure.com/databricks-certified-associate-developer-for-apache-spark-3-0-databricks-certified-associate-developer-for-apache-spark-3-0-exam-questions.html

## 시용자 정의 함수

```python
spark.udf.register("ACCESS_PERFORMANCE", assessPerformance)
spark.sql("SELECT customerSatisfactgion, ASSESS_PERFORMANCE(customerSatisfaction) AS result FROM stores")
```

```python
assessPerformanceUDF = udf(assessPerformance, IntegerType())
storedDF.withColumn("result", assessPerformanceUDF(col("customerSatisfaction")))
```

## UNIX epoch format에서 월(month) 추출

```python
storedDF.withColumn("openTimestamp", col("openDate").cast("Timestamp")) \
        .withColun("month", month(col("openTimestamp")))
```

## Join

> 스파크의 기본 join 구현은 `shuffled hash join`
  - 양쪽 RDD에서 같은 해시값의 키들이 같은 파티션에 모이도록 데이터를 이동(shuffle)

`df1.join(df2, joinExpression, joinType)`

```python
# inner join
df.join(newdf, df.id == newdf.id, "inner")
df1.join(df2, df1.col("id")==df2.col("id"), "inner")

# outer join
storesDF.join(employeesDF, "storeID", "outer")

# multiple keys
storesDF.join(employeesDF, ["storeId", "employeeId"])
```
> Join은 일상적으로 쓰이는 스파크의 연산 중 가장 비싼 축에 속한다. Join을 수행하기 전에 필터링을 적용하여 데이터의 크기를 최대한 줄여 놓으면 더 빠르게 join할 수 있다.


## Broadcast join

- Join하려는 두 테이블 중 하나가 다른 쪽보다 작은 경우 작은 쪽의 RDD를 큰 쪽의 worker node에 복사 --> join 시 발생하는 shuffle이 일어나지 않도록 하여 join 속도를 올림
  ```python
  transactionDf.join(broadcast(itemsDf), "transactionId", "left_semi")
  ```
- [[dev.data+ai.spark.config]]의 `spark.sql.autoBroadcastJoinThreshold` 설정으로 테이블을 자동으로 브로드캐스팅할수도 있음

## Explode

```
+------+-----------------------------+-------------------+
|itemId|attributes                   |supplier           |
+------+-----------------------------+-------------------+
|1     |[blue, winter, cozy]         |Sports Company Inc.|
|2     |[red, summer, fresh, cooling]|YetiX              |
|3     |[green, summer, travel]      |Sports Company Inc.|
+------+-----------------------------+-------------------+
```

```python
articlesDf.select(explode(col('attributes))) \
          .groupBy('col').count() \
          .sort('count', ascending=False) \
          .select('col')
```

```
+-------+
| col   |
+-------+
| summer|
| winter|
| blue  |
| cozy  |
| travel|
| fresh |
| red   |
| cooling|
| green |
+-------+
```

## 그룹에서 순위

```scala
// 데이터
val peopleDF = Seq(
  ("Ali", 0, Seq(100)),
  ("Barbara", 1, Seq(300, 250, 100)),
  ("Cesar", 1, Seq(350, 100)),
  ("Dongmei", 1, Seq(400, 100)),
  ("Eli", 2, Seq(250)),
  ("Florita", 2, Seq(500, 300, 100)),
  ("Gatimu", 3, Seq(300, 100))
).toDF("name", "department", "score")

// 기대 결과
|department| name |highest|
| 0| Ali| 100|
| 1|Dongmei| 400|
| 2|Florita| 500|
| 3| Gatimu| 300|

// 솔루션
import org.apache.spark.sql.expressions.Window
val windowSpec = Window.partitionBy("department").orderBy(col("score").desc)

peopleDF
.withColumn("score", explode(col("score")))
.select(col("department"),col("name"),dense_rank().over(windowSpec).alias("rank"), max(col("score")).over(windowSpec).alias("highest"))
.where(col("rank") === 1)
.drop("rank")
.orderBy("department")
.show()
```