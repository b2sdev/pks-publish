---
id: v7q8a35jkouboemyj9j27jd
title: Pandas Dataframe
desc: ''
updated: 1669268801109
created: 1669268101204
---

## Dataframe 생성

### 2개의 numpy로 dataframe 생성

```python
df = pd.DataFrame({'x': x, 'y': y})
```

## Indexing

### 특정 컬럼
```python
series <- df.loc[:, 'col_name']
dataframe <- df[['col1_name', 'col2_name']] 
```

## 데이터 제거

### 컬럼 제거

```python
df.drop('col_name', inplace=True, axis=1)
```

## Python 자료구조로 변환

### 특정 컬럼을 리스트로
```python
value_list = df.loc[:, 'col_name'].values
```


## One-hot encoding

```python
pd.get_dummies(df, columns=['col1_name', 'col2_name'])
```