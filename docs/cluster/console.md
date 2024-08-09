(cluster-console)=
# Console

The Console in CrateDB Cloud allows users to execute SQL queries seamlessly
against their CrateDB cluster. The Console can be accessed by users having the
"Organization Admin" role in the left-hand navigation menu within a cluster.

- **Table and Schema Tree View:** Easily navigate through your database 
  structure.
- **Client-Side Query Validation:** Ensure your SQL queries are correct before 
  execution.
- **Multiple Query Execution:** Run several queries in sequence.
- **Query History:** Access and manage your past queries.

:::{important}
- The Console is available for all newly deployed clusters.
- For older clusters, this feature can be enabled on demand. Contact 
  [support](https://support.crate.io/) for activation.
  
The Console currently utilizes a dedicated database user `gc_admin` with full 
cluster privileges.
:::

:::{note}
**Multi-Query Execution:**
When running multiple queries at once, the Console executes them sequentially, 
not within a single session or transaction. If one query fails, the subsequent 
queries will not be executed. Currently, session settings are not persisted 
between queries.
:::
