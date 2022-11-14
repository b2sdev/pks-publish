---
id: st4q3726xwavhzpa13npxir
title: Datetime
desc: ''
updated: 1668456642116
created: 1668217311439
---

## 날짜에서 년/월/일 추출
- Accessor `dt` 사용

```python
df['year'] = dt['date'].dt.year
df['month'] = dt['date'].dt.month
df['day'] = dt['date'].dt.day
```

## References
- https://pandas.pydata.org/pandas-docs/stable/reference/series.html#api-series-dt