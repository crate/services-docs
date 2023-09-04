(index)=
(cloud-docs-index)=

# CrateDB Cloud

**CrateDB Cloud** is a fully-managed service, allowing you to deploy, monitor,
back up, and scale your [CrateDB] clusters in the cloud without the need to do
database management yourself. You can store and analyze massive amounts of data
in near real-time, even with complex queries.

Users around the world rely on CrateDB Cloud clusters to store billions of records
and terabytes of data, all accessible without delays. If you want to start using
CrateDB Cloud, or make the most of your existing subscription, we are maintaining
resources and tutorials to support you correspondingly.


## Get started

Before you can start using CrateDB Cloud, you need to sign up for a user account.

::::{grid} 1 2 2 3
:margin: 4 4 0 0
:gutter: 1


:::{grid-item-card} {octicon}`person` Sign Up
:link: sign-up
:link-type: ref

Sign up to create and manage CrateDB clusters and other
CrateDB Cloud products. 
:::


:::{grid-item-card} {octicon}`rocket` Free Trial
:link: free-trial-budget
:link-type: ref

Learn how to sign up to get started with free credits
on the trial budget plan.
:::


::::


## Manage

CrateDB Cloud is fully-managed in day-to-day operations. For interacting with
your clusters using high-level commands, and to monitor their status, there is
a web-based control center, a HTTP API, and a command-line program.

::::{grid} 1 2 2 3
:margin: 4 4 0 0
:gutter: 1


:::{grid-item-card} {octicon}`unfold` Deploy
:link: cluster-deployment
:link-type: ref

Deploy a CrateDB cluster.
:::


:::{grid-item-card} {octicon}`infinity` Scale
:link: reconfigure-cluster
:link-type: ref

Learn about the available options to scale your clusters.
:::


:::{grid-item-card} {octicon}`tools` Manage
:link: cloud-howtos-index
:link-type: ref

Learn about general information how to manage your cluster.
:::


:::{grid-item-card} {octicon}`table` Web Console
:link: console-overview
:link-type: ref

The web-based management console for all your managed and on-premise
clusters.
:::


:::{grid-item-card} {octicon}`terminal` Croud CLI
:link: cluster-deployment-croud
:link-type: ref

A command-line based terminal program to operate your managed clusters.
:::


:::{grid-item-card} {octicon}`container` CrateDB Edge
:link: edge
:link-type: ref

Integrate the CrateDB Cloud software stack with on-premise infrastructure.
:::


::::


Quick start.

::::{grid} 1 2 2 3

:::{grid-item-card} {octicon}`table;2em` CrateDB Cloud Console
:columns: 12
:link: https://console.cratedb.cloud/
:link-type: url

Directly navigate to the CrateDB Cloud Console.
https://console.cratedb.cloud/
:::

::::


## Connect

This section introduces you to the canonical set of database drivers, client-
and developer-applications, and how to configure them to connect to CrateDB.
Just to name a few, it is about the CrateDB Admin UI, `crash`, `psql`,
DataGrip, and DBeaver applications, the Java/JDBC/Python drivers, the SQLAlchemy
and Flink dialects, and more.

CrateDB integrates well with a diverse set of applications and tools concerned
with analytics, visualization, and data wrangling, in the areas of ETL, BI, 
metrics aggregation and monitoring, and more.


::::{grid} 1 2 2 2
:margin: 4 4 0 0
:gutter: 1


:::{grid-item-card} {material-outlined}`table_chart;2em` Admin UI
:link: crate-admin-ui:index
:link-type: ref

Each CrateDB Cloud cluster offers a dedicated Admin UI, which can be used to explore
data, schema metadata, and cluster status information.
:::

:::{grid-item-card} {material-outlined}`link;2em` Clients, Tools, and Integrations
:link: crate-clients-tools:index
:link-type: ref

Learn about compatible client applications and tools, and how to configure
your favorite client library to connect to a CrateDB cluster.
:::


::::


Quick start.

::::{grid} 1 2 2 3

:::{grid-item-card} {octicon}`file-code;2em` Import data
:columns: 12
:link: https://community.crate.io/t/importing-data-to-cratedb-cloud-clusters/1467
:link-type: url

Learn how to import data into your CrateDB Cloud clusters.
:::

::::


```{note}
Like [CrateDB itself], this is an open source documentation project. [Suggestions
for improvements], and [source code contributions], are always welcome. {fab}`github`
```


```{toctree}
:maxdepth: 1
:hidden:

Sign Up <tutorials/sign-up>
Free Trial <tutorials/promotions/free-trial-budget>
Deploy <tutorials/deploy/index>
Scale <howtos/reconfigure-cluster>
Manage <howtos/index>
Web Console <reference/overview>
Croud CLI <tutorials/deploy/croud>
tutorials/edge/index
```

```{toctree}
:maxdepth: 1
:hidden:

reference/index
```


[CrateDB]: https://crate.io/product/
[Croud CLI]: https://crate.io/docs/cloud/cli/
[How-To Guides]: https://crate.io/docs/cloud/en/latest/howtos/
[Reference]: https://crate.io/docs/cloud/en/latest/reference/
[CrateDB itself]: https://github.com/crate/crate
[source code contributions]: https://github.com/crate/cloud-docs/tree/main/docs
[suggestions for improvements]: https://github.com/crate/cloud-docs/issues
