---
id: krw7dpkjkiu6sesrnypgdky
title: Memo
desc: ''
updated: 1667827810528
created: 1667827616739
---

```python
import warnings
warnings.filterwarnings('ignore') 
```

## pd.
```python
pd.read_csv('...', index_col=0)
pd.isnull(df['col_name'])
pd.DataFrame({'Id': test1['Id'], 'SalePrice': preds_test})
new_df = pd.DataFrame(data=df, columns=df.columns) 
pd.to_datetime(df['dt'])
pd.set_option("display.max_columns", 101) 
pd.to_numeric(varible_split.str.get(2), errors='coerce') 
pd.concat([df1, df2], axis=1) 
pd.date_range(start='05-01-2021', end='05-12-2021') 
```

## DataFrame 전체
```python
df.copy()
df.shape 
df.info()
df.head()
df.describe(include='all').T
df.dtypes
df.dtypes.value_counts() 
df.isnull().sum()
df.set_index('id') or df['id'] = df.index 
df.corr() 
df.filter(['col_1', 'col_2'], axis=1)  
df.drop(['col_1', 'col_2'], axis=1, inplace=True)
data.drop(data.loc[(data['SalePrice'] < 200000) & (data['GrLivArea'] > 4000)].index) 
df.to_csv('submission.csv', index=False)
numeric_ = df.select_dtypes(exclude=['object']).drop(['MSSubClass'], axis=1).copy()
cat_train = X.select_dtypes(include=['object']).copy()
cat_train['MSSubClass'] = X['MSSubClass'] 
df.isnull().sum().sort_values(ascending=False)
df.columns = ['col_1', 'col_2'] 
df.select_dtypes('object').apply(pd.Series.nunique, axis=0) 
df.sort_values(by=['id', 'age'], ascending=False) 
df.reset_index 
```

## 일부 컬럼
```python
df['col_name'].value_counts()
df['col_name'].fillna(0) .fillna('TA')
df['col_name'].apply(str)
df['col'].map({'Ex': 3, 'Gd': 2, 'Fa': 1})
df['col'].replace(mapper, inplace=True) 

df['col_sum'] = df['col_1'] + df['col_2'] 
df['col'] = df.apply(lambda x: x['col1'] if pd.isnull(x['col2']) else x['col1'] + x['col2'], axis=1)

df['col'].astype(int).plot.hist()

df['col'].str.split()  
df.loc[:, 'col'] 
```

## 일부 로우
```python
df.loc[df.Sex=='female']
df.loc[df.Sex=='female']['Survived']
df.iloc[[0, 2], :]
df.loc[df.age >= 24]  
df[df.iloc[:, 1] != 0].sort_values('col', ascending=False).round(1) 
```

## Iterate
```python
for index, row in df.iterrows():
	...

for index in df.index:
	if np.isnan(df.loc[i, 'inflation_annual']):
		...  
```

## groupby
```python
df.groupby('col')['salary'].mean()  
```

## unique categories
```python
for col_name in df1.columns:
    if df1[col_name].dtypes == 'object':
        unique_cat = len(df1[col_name].unique())
        print(f'{col_name}: {unique_cat}')
```

## missing values
```python
mis_val = app_train.isnull().sum()
mis_val_percent = 100 * app_train.isnull().sum() / len(app_train)
mis_values = pd.concat([mis_val, mis_val_percent], axis=1)
mis_values.columns = ['Missing Values', '% of Total Values']
mis_values = mis_values[mis_values.iloc[:, 1] != 0].sort_values('% of Total Values', ascending=False).round(1)
mis_values.head(20) 
```

## Number of unique classes in each object column 
```python
df.select_dtypes('object').apply(pd.Series.nunique, axis=0)  
```