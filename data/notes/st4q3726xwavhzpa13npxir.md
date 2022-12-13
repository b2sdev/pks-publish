
## 날짜에서 년/월/일 추출
- Accessor `dt` 사용

```python
df['year'] = dt['date'].dt.year
df['month'] = dt['date'].dt.month
df['day'] = dt['date'].dt.day
```

## References
- https://pandas.pydata.org/pandas-docs/stable/reference/series.html#api-series-dt