
## 결측치 확인

```python
df.info()
df.isnull().sum()
```

## 결측치 제거

`DataFrame.dropna(axis=0, how='any', thresh=None, subset=None, inplace=False)`
- axis=1 : 컬럼을 기준으로 동작
- how='any' : 결측치가 하나라도 포함된 행 삭제
- how='all' : 모든 데이터가 결측치인 행 삭제
- thresh=숫자 : 숫자 이상의 데이터를 가진 행은 삭제하지 않음
- subset=['col_name1', 'col_name2', ...] : subset으로 대상 컬럼 지정

```python
df_dropped = df.dropna(how='all', subset=['col1', 'col2', 'col3'])

# 제거된 행의 개수 확인
print(len(df) - len(df_dropped))
```

## 결측치 대체 (TBD)