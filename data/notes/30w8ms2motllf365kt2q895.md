


## High-level architecture

![](https://docs.databricks.com/_images/databricks-architecture.png)

## Control plane and data plane

- The control plane includes the backend services that Databricks manages in its own AWS account. Notebook commands and many other workspace configurations are stored in the control plane and encrypted at rest.

- The data plane is where your data is processed.
    - For most Databricks computation, the compute resources are in your AWS account in what is called the Classic data plane. This is the type of data plane Databricks uses for notebooks, jobs, and for Classic Databricks SQL warehouses.


## Reference
- https://docs.databricks.com/getting-started/overview.html