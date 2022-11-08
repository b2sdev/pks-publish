---
id: 1y1yaydbzccdy4uu5qkpjt2
title: Memo (TBD)
desc: ''
updated: 1667827919523
created: 1667827919523
---

> 정리 필요

```python
   
1. Imputation

threshold = 0.7

# Dropping columns with missing value rate higher than threshold
data = data[data.columns[data.isnull().mean() < threshold]

# Dropping rows with missing value rate higher than threshold
data = data.loc[data.isnull().mean(axis=1) < threshold]

# Filling all missing values with 0
data = data.fillna(0)

# Filling missing values with medians of the columns
data = data.fillna(data.median())

# Max fill function for categorical columns
data['column_name'].fillna(data['column_name'].value_counts().idxmax(), inplace=True)

2. Hangling Outliers

# Dropping the outlier rows with standard deviation
factor = 3
upper_lim = data['column'].mean() + data['column'].std() * factor
upper_lim = data['column'].mean() + data['column'].std() * factor

data = data[(data['column'] < upper_lim) & (data['column'] > lower_lim) ]       

# Dropping the outlier rows with Percentiles
upper_lim = data['column'].quantile(.95)
lower_lim = data['column'].quantile(.05)

data = data[(data['column'] < upper_lim) & (data['column'] > lower_lim)]

3. Binning

# Numerical Binning Example

Value	   Bin
0-30	-> Low
31-70	-> Mid
71-100	-> High     

# Categorical Binning Example

Value	   Bin
Spain	-> Europe
Italy	-> Europe
Chile	-> South America
Brazil	-> South America      

# Numerical Binning Example

data['bin'] = pd.cut(data['value'], bins=[0,30,70,100], labels=["Low", "Mid", "High"])

    value   bin
 0      2   Low
 1     45   Mid
 2      7   Low
 3     85  High
 4     28   Low  

# Categorical Binning Example

      Country
 0      Spain
 1      Chile
 2  Australia
 3      Italy
 4     Brazil   

conditions = [
	data['Country'].str.contains('Spain'),
	data['Country'].str.contains('Italy'),
	data['Country'].str.contains('Chile'),
	data['Country'].str.contains('Brazil')  
]

choices = ['Europe', 'Europe', 'South America', 'South America']  

data['Continent'] = np.select(conditions, choices, default='Other') 

4. Log Transform

...

5. One-hot encoding

encoded_columns = pd.get_dummies(data['column'])
data = data.join(encoded_columns).drop('column', axis=1)

6. Group Operations

data.groupby('id').agg(lambda x: x.value_counts().index[0])

# Pivot table Pandas Example

data.pivot_table(index='column_to_group', columns='column_to_encode', values='aggregation_column', aggfunc=np.sum, fill_value = 0)

grouped = data.groupby('column_to_group')

sums = grouped[sum_cols].sum().add_suffix('_sum')
avgs = grouped[mean_cols].mean().add_suffix('_avg')

new_df = pd.concat([sums, avgs], axis=1)  

7. Feature Split

data.name.str.split(" ").map(lambda x: x[0])
data.name.str.split(" ").map(lambda x: x[-1]) 

data.title.head()

data.title.str.split("(", n=1, expand=True)[1].str.split(")"), n=1, expand=True)[0]

8. Scaling

# Normalization

data = pd.DataFrame({'value': [2, 45, -23, 85, 28, 2, 35, -12})      

data['normalized'] = (data['value'] - data['value'].min()) /
	(data['value'].max() - data['value'].min())

# Standardization

data['standardized'] = (data['value'] - data['value'].mean()) / 
	data['value'].std()

9. Extracting Date

from datetime import date

data = pd.DataFrame({'date':['01-01-2017','04-12-2008','23-06-1988','25-08-1999','20-02-1993',]})

# Transform string to date
data['date'] = pd.to_datetime(data.date, format="%d-%m-%Y")

# Extracting Year
data['month'] = data['date'].dt.year

# Extracting Month
data['month'] = data['date'].dt.month

# Extracting passed years since the date 
data['passed_years'] = date.today().year - data['date'].dt.year

# Extracting passed months since the date
data['passed_months'] = (date.today().year - data['date'].dt.year) * 12 + date.today().month - data['date'].dt.month

# Extracting the weekday name of the date
data['day_name'] = data['date'].dt.day_name() 

=======

# Drop columns that have too many missing value 
null = train.isnull().sum()
train1 = train
test1 = test
train1.drop(columns=['aaa', 'bbb', 'ccc'], axis=1, inplace=True)
test1.drop(columns=['aaa', 'bbb', 'ccc'], axis=1, inplace=True)

# y, X 설정
y = train1['SalePrice']
X = train1.drop('SalePrice', axis=1, inplace=True)

# boolean field 설정
train1['Fence'].unique()
fence_map = {'MnPrv':1, 'GdWo':1, 'GdPrv':1, 'MnWw':1}
train1['Fence'] = train1['Fence'].map(fence_map)
test1['Fence'] = test1['Fence'].map(fence_map)

# null 처리
train1['Fence'] = train1['Fence'].fillna(0)     
test1['Fence'] = test1['Fence'].fillna(0)

train1['GarageCond'].value_counts()
train1['GarageCond'] = train1['GarageCond'].fillna('TA')
test1['GarageCond'] = test1['GarageCond'].fillna('TA')

# 숫자를 문자열로 변환
train1['MoSold'] = train1['MoSold'].apply(str)

# 컬럼의 값의 개수
test['MSZoning'].value_counts()

# 컬럼 두 개를 하나로 합치기(Merge)
train1['Condition'] = train1.apply(lambda x: x['Condition1'] if (pd.isnull(x['Condition2'])) else str(x['Condition1'] + '-' + str(x['Condition2]), axis=1)
train1.drop(['Condition1', 'Condition2']), axis=1, inplace=True) 
     
===== 

def date_preprocessing(dataframe):
    df = dataframe.copy()
    df['일자'] = pd.to_datetime(df['일자'])
    df['년도'] = df['일자'].dt.year
    df['월'] = df['일자'].dt.month
    df['일'] = df['일자'].dt.day
    df['주'] = df['일자'].dt.weekday
    return df   
```