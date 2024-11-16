(feature)=
(features)=
(all-features)=
# All Features

All features of [CrateDB Cloud] at a glance.

:::::{grid} 1 3 3 3
:margin: 4 4 0 0
:padding: 0
:gutter: 2
:class-container: compact

::::{grid-item-card} {material-outlined}`power_settings_new;2em` Functional
:class-footer: text-smaller

- [SQL Database][Database Features]
:::{toctree}
:maxdepth: 1

SQL Console <../cluster/console>
../cluster/automation
../cluster/import
../cluster/export
API <../organization/api>
API CLI <../tutorials/deploy/croud>
:::
+++
CrateDB Cloud includes enhanced automation and productivity features,
and a wide range of integrations with data ingestion and
visualization tools.
::::

::::{grid-item-card} {material-outlined}`assured_workload;2em` Operational
:class-footer: text-smaller

:::{toctree}
:maxdepth: 1

Management Console <../cluster/manage>
Automatic Backups <../cluster/backups>
:::
- Monitoring
- Marketplace Coverage

  [AWS][AWS Marketplace], [Azure][Azure Marketplace], [GCP][GCP Marketplace]
- [Support Plans]


- Effortless Scaling
- Zero Downtime Upgrades
- Flexible Deployment: Full-managed vs. hybrid
- Cost-effectiveness
+++
CrateDB Cloud provides confident scaling of your workloads,
and deployments on your preferred infrastructure provider.
::::

::::{grid-item-card} {material-outlined}`security;2em` Security
:class-footer: text-smaller

CrateDB Cloud is [secure, certified, and compliant].
- [Encryption]
- [RBAC]
- [Auditing]
- [ISO 27001]
- [SOC 2 Type 2]
- [HIPAA]
- [GDPR]
- [CCPA]
+++
CrateDB Cloud ensures secure data management with its encryption and
authentication mechanisms, and its operational certifications.
::::

:::::



:::{rubric} Learn
:::
If you want to start using CrateDB Cloud, or make the most of your
existing subscription, we are maintaining resources and tutorials
to support you correspondingly.


:::::{grid} 2
:margin: 3
:gutter: 2

::::{grid-item}

:::{card} {octicon}`tools` Manage
:link: cloud-howtos-index
:link-type: ref
Learn how to manage your cluster.
:::

:::{card} {octicon}`codespaces` API
:link: api
:link-type: ref
Programmatic access to CrateDB Cloud services.
:::

:::{card} {octicon}`terminal` API CLI
:link: cluster-deployment-croud
:link-type: ref
CrateDB Cloud services from the command-line.
:::

::::

::::{grid-item}

:::{card} {octicon}`table` SQL Console
:link: cluster-console
:link-type: ref
Explore data and execute SQL queries.
:::

:::{card} {octicon}`file-code` Import
:link: cluster-import
:link-type: ref
Import data into your CrateDB Cloud cluster.
:::

:::{card} {octicon}`file-code` Export
:link: cluster-export
:link-type: ref
Export data from your CrateDB Cloud cluster.
:::

::::

:::::


Learn about key database drivers and client applications for CrateDB,
such as CrateDB Admin UI, crash, psql, DataGrip, and DBeaver.
Discover how to configure these tools and explore CrateDB's compatibility
with analytics, ETL, BI, and monitoring solutions.


::::{grid} 1 2 2 3
:margin: 4 4 0 0
:gutter: 2


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

::::


[Auditing]: https://cratedb.com/product/features/auditing
[AWS Marketplace]: https://aws.amazon.com/marketplace/pp/prodview-l7rqf2xpeaubk
[Azure Marketplace]: https://azuremarketplace.microsoft.com/en-us/marketplace/apps/crate.cratedbcloud?tab=overview
[CCPA]: https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.140.
[CrateDB Cloud]: https://cratedb.com/product/cloud
[Database Features]: https://cratedb.com/docs/guide/feature/
[Encryption]: https://cratedb.com/product/features/data-encryption
[GCP Marketplace]: https://console.cloud.google.com/marketplace/product/cratedb-public/cratedb-gcp
[GDPR]: https://gdpr-info.eu/
[HIPAA]: https://www.cdc.gov/phlp/php/resources/health-insurance-portability-and-accountability-act-of-1996-hipaa.html?CDC_AAref_Val=https://www.cdc.gov/phlp/publications/topic/hipaa.html
[ISO 27001]: https://cratedb.com/blog/cratedb-elevates-its-security-standards-and-achieves-iso-27001-certification
[RBAC]: https://cratedb.com/product/features/authorization
[secure, certified, and compliant]: https://cratedb.com/contact/security
[SOC 2 Type 2]: https://cratedb.com/blog/soc-2-type-2-compliance 
[Support Plans]: https://cratedb.com/support/support-plans


<!--
Custom styles.
TODO: Possibly upstream to crate-docs-theme.
-->
<style>
.compact ul {
  margin-top: 0;
  margin-bottom: 0;
}
</style>
