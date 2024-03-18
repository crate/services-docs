(index)=
(cloud-docs-index)=

# CrateDB Cloud

CrateDB Cloud is a fully managed, terabyte-scale, and cost-effective
analytics database that lets you run analytics over vast amounts of
data in near real time, even with complex queries.

It is an SQL database service for enterprise data warehouse workloads,
that works across clouds and scales with your data.


:::::{grid}
:padding: 0

::::{grid-item}
:class: rubric-slimmer
:columns: 6

:::{rubric} Database Features
:::
CrateDB Cloud helps you manage and analyze your data with procedures
like machine learning, geospatial analysis, and business intelligence.

CrateDB Cloud's scalable, distributed analysis engine lets you query
terabytes worth of data efficiently.

CrateDB provides a rich data model including container-, geospatial-, and
vector-data types, and capabilities for full-text search.
::::

::::{grid-item}
:class: rubric-slimmer
:columns: 6

:::{rubric} Operational Benefits
:::
CrateDB Cloud is a fully managed enterprise service, allowing you to deploy,
monitor, back up, and scale your CrateDB clusters in the cloud without the
need to do database management yourself.

With CrateDB Cloud, there's no infrastructure to set up or manage, letting you
focus on finding meaningful insights using plain SQL, and taking advantage of
flexible pricing models across on-demand and flat-rate options.
::::

:::::


:::{rubric} Learn
:::
Users around the world rely on CrateDB Cloud clusters to store billions of records
and terabytes of data, all accessible without delays. If you want to start using
CrateDB Cloud, or make the most of your existing subscription, we are maintaining
resources and tutorials to support you correspondingly.


::::{grid} 1 2 2 3
:margin: 4 4 0 0
:gutter: 1


:::{grid-item-card} {octicon}`rocket` Quick Start
:link: quick-start
:link-type: ref

Learn how to sign up and get started with a free cluster.
:::


:::{grid-item-card} {octicon}`mortar-board` Tutorials
:link: tutorials
:link-type: ref

Learn how to use key features of CrateDB.
:::



:::{grid-item-card} {octicon}`tools` Manage
:link: cloud-howtos-index
:link-type: ref

Learn how to manage your cluster.
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


:::{grid-item-card} {octicon}`container` CrateDB Cloud on Kubernetes
:link: cloud-on-kubernetes
:link-type: ref

Run your own CrateDB Cloud region using Kubernetes.
:::


::::


Do you want to learn about key database drivers and client applications for 
CrateDB, such as CrateDB Admin UI, crash, psql, DataGrip, and DBeaver? Discover
how to configure these tools and explore CrateDB's compatibility with analytics,
ETL, BI, and monitoring solutions.


::::{grid} 1 2 2 3
:margin: 4 4 0 0
:gutter: 1


:::{grid-item-card} {material-outlined}`table_chart` Admin UI
:link: crate-admin-ui:index
:link-type: ref

Each CrateDB Cloud cluster offers a dedicated Admin UI, which can be used to explore
data, schema metadata, and cluster status information.
:::

:::{grid-item-card} {material-outlined}`link` Clients, Tools, and Integrations
:link: crate-clients-tools:index
:link-type: ref

Learn about compatible client applications and tools, and how to configure
your favorite client library to connect to a CrateDB cluster.
:::

:::{grid-item-card} {octicon}`file-code` Import data
:link: https://community.crate.io/t/importing-data-to-cratedb-cloud-clusters/1467
:link-type: url

Learn how to import data into your CrateDB Cloud clusters.
:::

::::


:::{note}
Like [CrateDB itself], this is an open source documentation project. [Suggestions
for improvements], and [source code contributions], are always welcome. {fab}`github`
:::


:::{toctree}
:maxdepth: 1
:hidden:

Quick Start <tutorials/quick-start>
Tutorials <tutorials/index>
Services <reference/services>
Manage <howtos/index>
Web Console <reference/overview>
Croud CLI <tutorials/deploy/croud>
tutorials/edge/index
Reference <reference/index>
:::

[CrateDB]: https://crate.io/product/
[Croud CLI]: https://crate.io/docs/cloud/cli/
[How-To Guides]: https://crate.io/docs/cloud/en/latest/howtos/
[Reference]: https://crate.io/docs/cloud/en/latest/reference/
[CrateDB itself]: https://github.com/crate/crate
[source code contributions]: https://github.com/crate/cloud-docs/tree/main/docs
[suggestions for improvements]: https://github.com/crate/cloud-docs/issues
