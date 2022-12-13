
## DBFS

```
databricks fs cp a.file dbfs:/path/to/a.file
dbfs cp a.file dbfs:/FileStore/a.file
```

## Workspace
```
databricks workspace ls /Users/someone@example.com/example -l
dababricks workspace import a.file /Users/someone@example.com/path/to/a.file -l PYTHON -f JUPYTER
```


## Reference
- https://docs.databricks.com/dev-tools/cli/workspace-cli.html