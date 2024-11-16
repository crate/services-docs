(index)=
(cloud-docs-index)=

# CrateDB Cloud

[CrateDB Cloud] is a fully managed, terabyte-scale, and cost-effective
analytics database that lets you run analytics over vast amounts of
data in near real time, even with complex queries.

It is an SQL database service for enterprise data warehouse workloads,
that works across clouds and scales with your data.


:::::{grid}
:padding: 0

::::{grid-item}
:class: rubric-slimmer
:columns: 6

:::{rubric} Database Service Features
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


::::{grid}

:::{grid-item}
:columns: 7
![image](https://cratedb.com/hs-fs/hubfs/cloud-edge-config.png?width=480)
:::
:::{grid-item}
:columns: 5
![image](https://cratedb.com/hs-fs/hubfs/CrateDB-Security-Certifications-Logos.png?width=320)
![image](https://cratedb.com/hs-fs/hubfs/CrateDB-Cloud-Integrations.png?width=320)
:::

::::


::::{grid} 1 2 2 2
:margin: 4 4 0 0
:padding: 0
:gutter: 2


:::{grid-item-card} {material-outlined}`description;2em` All Features
:link: all-features
:link-type: ref
:link-alt: All features of CrateDB Cloud
:class-footer: text-smaller

- Functional: SQL Database, SQL Console, Automation, Import, Export, API
- Operational: Management Console, Automatic Backups, Marketplaces AWS, Azure, GCP,
  Support Plans
- Security: Encryption, RBAC, Auditing, Certifications
+++
**What's inside:**
All features of CrateDB Cloud on one page.
:::


:::{grid-item-card} {material-outlined}`rocket;2em` Quick Start
:link: quick-start
:link-type: ref
:link-alt: Sign up and get started with CrateDB Cloud
:class-footer: text-smaller

Users around the world rely on CrateDB Cloud clusters to store billions of records
and terabytes of data, all accessible without delays.
<br><br>
```{button-link} https://example.com
:color: primary
:expand:
**Start using CrateDB Cloud now**
```
+++
**What's inside:**
Learn how to sign up and get started.
:::

::::



:::{rubric} Resource Access
:::

::::::{grid} 2

:::{grid-item-card} CrateDB Cloud Console
:link: https://console.cratedb.cloud/
:link-type: url
:margin: 0
:padding: 0

![image](/_assets/img/cluster-manage.png)

Access the management console of CrateDB Cloud.
+++
```{image} https://console.cratedb.cloud/static/media/login_logo.29bc89cf03a01ccf3ed2aa57b8a4e1c1.svg
:class: bg-primary
:height: 20px
:align: center
```
:::

:::::{grid-item}

::::{grid} 1
:gutter: 3

:::{grid-item-card}
:link: https://aws.amazon.com/marketplace/pp/prodview-l7rqf2xpeaubk
:link-type: url
```{image} /_assets/logo/aws-marketplace.png
:class: bg-primary
:height: 60px
:align: center
```
CrateDB Cloud on AWS Marketplace.
:::

:::{grid-item-card}
:link: https://azuremarketplace.microsoft.com/en-us/marketplace/apps/crate.cratedbcloud
:link-type: url
```{image} /_assets/logo/microsoft.png
:height: 60px
:align: center
```
CrateDB Cloud on Azure Marketplace.
:::


:::{grid-item-card}
:link: https://console.cloud.google.com/marketplace/product/cratedb-public/cratedb-gcp
:link-type: url
```{image} /_assets/logo/google-cloud.png
:height: 60px
:align: center
```
CrateDB Cloud on Google Cloud Marketplace.
:::

::::

:::::
::::::


:::{toctree}
:maxdepth: 1
:hidden:

All Features <feature/index>
Quick Start <tutorials/quick-start>
Services <reference/services>
Console <cluster/console>
Automation <cluster/automation>
Import <cluster/import>
Export <cluster/export>
Backups <cluster/backups>
Manage Cluster <cluster/manage>
Billing <organization/billing>
API <organization/api>
API CLI <tutorials/deploy/croud>
How Tos <howtos/index>
tutorials/edge/index
Reference <reference/index>
:::


[CrateDB]: https://crate.io/product/
[CrateDB Cloud]: https://cratedb.com/product/cloud
[Croud CLI]: https://crate.io/docs/cloud/cli/
[How-To Guides]: https://crate.io/docs/cloud/en/latest/howtos/
[Reference]: https://crate.io/docs/cloud/en/latest/reference/
