---
id: c1e5yqaofug0sowxvnsspui
title: Pyodbc
desc: ''
updated: 1666959920354
created: 1666959920354
---

### #1. msodbcsql17과 pyodbc를 설치하여 사용

```python
%sh
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get -q -y install msodbcsql17
sudo apt-get install msodbcsql17
```

```python
%pip install pyodbc
```


```python
import pyodbc

try:
    conn = pyodbc.connect('DRIVER={ODBC Driver 17 for SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
    cursor = cnxn.cursor()
    cursor.execute("…")
except Exception as e:
    print(e)
```

### #2. Databricks에서 제공하는 connector 사용 

* TBD