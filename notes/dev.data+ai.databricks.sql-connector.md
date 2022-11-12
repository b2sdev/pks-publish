---
id: gaf44w0jm155ojabiyonsv6
title: Databricks SQL Connector
desc: ''
updated: 1668240903610
created: 1662560640000
---


The Databricks SQL Connector for Python is a Python library that allows you to use Python code to run SQL commands on Databricks clusters and Databricks SQL warehouses.

## Install the library

```cmd
pip install databricks-sql-connector
```

## Query data

```python
from databricks import sql
import os

with sql.connect(server_hostname = os.getenv("DATABRICKS_SERVER_HOSTNAME"),
                 http_path       = os.getenv("DATABRICKS_HTTP_PATH"),
                 access_token    = os.getenv("DATABRICKS_TOKEN")) as connection:

  with connection.cursor() as cursor:
    cursor.execute("SELECT * FROM default.diamonds LIMIT 2")
    result = cursor.fetchall()

    for row in result:
      print(row)
```

## References
- https://docs.databricks.com/dev-tools/python-sql-connector.html#get-started