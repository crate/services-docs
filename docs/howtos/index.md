(cloud-howtos-index)=

# How-To Guides


This is a collection of how-to guides for CrateDB Cloud. Learn how to manage
your cluster and organizations below. For the purposes of these guides, 
we assume you interact with CrateDB Cloud by using the CrateDB
Cloud Console. Alternatively, you can use the command-line interface CrateDB
Cloud CLI, aka. {ref}`Croud <cloud-cli:index>`.


````{note}
Not all operations supported by the CrateDB Cloud Console are also
available via Croud. Most importantly, clusters can only be deployed via
the CrateDB Cloud Console.
````

```{toctree}
:hidden:
:maxdepth: 1

Create Organization <create-org>
Add users to organization <add-users>
Reconfigure Cluster <reconfigure-cluster>
Suspend Cluster <suspend-cluster>
Delete Cluster <delete-cluster>
Restore Backups <restore-backups>
Logical Replication <logical-replication>
Private Endpoints <private-endpoints>
```

## Organization Management

::::{grid} 2 2 2 3
:margin: 4 4 0 0
:gutter: 1

:::{grid-item-card} {octicon}`organization` Create Organization
:link: create-org
:link-type: ref
Learn how to create new organization with your account.
:::

:::{grid-item-card} {octicon}`person-add` Add Users to Organization
:link: add-users
:link-type: ref
Learn how to add users to organizations and manage their privileges.
:::

::::

## Cluster Management

::::{grid} 2 2 2 3
:margin: 4 4 0 0
:gutter: 1

:::{grid-item-card} {octicon}`tools` Reconfigure Cluster
:link: reconfigure-cluster
:link-type: ref
Learn how to scale your cluster up or down, depending on your needs.
:::

:::{grid-item-card} {octicon}`hourglass` Suspend Cluster
:link: suspend-cluster
:link-type: ref
Learn how to temporarily suspend your cluster. You are only charged for storage while in suspended state.
:::

:::{grid-item-card} {octicon}`trash` Delete Cluster
:link: delete-cluster
:link-type: ref
Learn how to permanently delete your cluster along with your data.
:::

:::{grid-item-card} {octicon}`sync` Restoring Backups
:link: restore-backups
:link-type: ref
Learn how backups are made and how to restore them.
:::

:::{grid-item-card} {octicon}`clock` Logical Replication
:link: logical-replication
:link-type: ref
Logical replication is a mechanism by which data can automatically be 
copied across multiple clusters.
:::

:::{grid-item-card} {octicon}`clock` Private Endpoints
:link: private-endpoints
:link-type: ref
A private endpoint, or private link, is a mechanism that allows a 
secure, private connection to your cluster.
:::

:::{grid-item-card} {octicon}`link` Clients, Tools, and Integrations
:link: crate-clients-tools:index
:link-type: ref

Learn about compatible client applications and tools, and how to configure
your favorite client library to connect to a CrateDB cluster.
:::

::::

````{note}
This is an open source documentation project. We host the source code and
issue tracker on [GitHub](https://github.com/crate/cloud-docs/) .
````