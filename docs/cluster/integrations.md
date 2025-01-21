(cluster-integrations)=
# Integrations

CrateDB Cloud simplifies data ingestion with fully managed integrations from
external data sources. Unlike traditional import jobs, integrations run
continuously, automatically importing new data into your CrateDB Cloud cluster
as it becomes available. This makes them ideal for real-time data
synchronization and keeping your database up to date with external systems.
Fully managed by CrateDB Cloud, integrations eliminate the need for manual
setup or maintenance of separate ETL pipelines.


```{figure} ../_assets/img/integrations-example.png
:width: 600px
:align: center
:alt: Integration in CrateDB Cloud
```

:::{toctree}
:maxdepth: 1
:hidden:

MongoDB CDC (Preview) <integrations/mongo-cdc>
:::

---

:::
## Key Concepts
:::

:::
### Integration
:::

An integration in CrateDB Cloud automatically imports data from an external data
source into a table within your CrateDB Cloud cluster. It uses a secure
connection to ensure data privacy and can run continuously to handle updates
in real time. You can create multiple integrations for the same data source to
support different tables or configurations.

Currently, CrateDB Cloud supports ingestion from the following data source:
- {ref}`MongoDB CDC (Preview) <integrations-mongo-cdc>`

More integrations are planned for future releases to expand the range of
supported data sources and use cases.

:::
### Connection
:::

A "Connection" in CrateDB Cloud associates authentication credentials with a
specific data source. This allows secure access to the external system and is
reusable across multiple integrations. By setting up a connection once, you can
streamline the process of creating and managing integrations without having to
re-enter credentials for each one.
