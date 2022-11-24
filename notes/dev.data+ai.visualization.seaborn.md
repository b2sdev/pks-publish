---
id: lyuotykr3e47c5bt119iyb5
title: Seabor
desc: ''
updated: 1669269147500
created: 1669268978751
---

## Import

```python
import seaborn as sns
```

## Distribution plot

```python
fig, (ax1, ax2) = plt.subplots(ncols=2)
fig.set_size_inches(12, 5)
sns.distplot(y_train, ax=ax1, bins=50)
ax1.set(title='train')
sns.distplot(pred, ax=ax2, bind=50)
ax2.set(title='test'))
```