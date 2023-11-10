(services)=

# Services

In the realm of CrateDB Cloud services, understanding your options is crucial
for optimizing both performance and costs. This section of the documentation
provides an in-depth look at the various service plans we offer, catering to a
wide range of use-cases from small-scale applications to enterprise-level
deployments. Our service plans are engineered for scalability, reliability, and
performance.

::::{grid} 1 2 2 3
:margin: 0 0 0 0
:gutter: 01

:::{grid-item-card} Shared
_non-critical workloads_

- Single Node
- Up to 8 shared vCPUs
- Up to 12 GiB RAM
- Up to 1 TiB storage
- Backups (once per day)
- Development support
:::

:::{grid-item-card} Dedicated
_production workloads_

- Up to 9 Nodes
- Up to 144 vCPUs
- Up to 495 GiB RAM
- Up to 72 TiB storage
- Backups (once per hour)
- Basic Support

---

- AWS / Azure Private Link
- Uptime SLAs
- Premium support available


:::

:::{grid-item-card} Custom
_large production workloads_

- Any cluster size
- Custom compute options
- Dedicated master nodes
- Unlimited Storage
- Custom Backups
- Premium Support
- AWS / Azure Private Link
- Uptime SLAs

<br>

[Contact us for more information](https://cratedb.com/contact)
:::

::::

## Shared

CrateDB Cloud's Shared Plan provides an affordable and easy-to-setup option for
users who require basic database functionalities. The plan is built around the
principle of cost-effectiveness and is particularly well-suited for development,
testing, or non-critical production environments.

**Node sizes**
:::{table}
:width: 700px
:widths: 200, 200, 100, 100
:align: left
| Plan | Size   | vCPUs     | RAM      |  Storage  |
|----|--------|-----------|----------| ---- |
| Shared | CRFREE* | up to 2 | 2 GiB    | 8 GiB |
| Shared | S2     | up to 2 | 2 GiB    | 8 GiB to 1TiB |
| Shared | S4     | up to 3 | 4 GiB    | 8 GiB to 1TiB |
| Shared | S6     | up to 4 | 6 GiB    | 8 GiB to 1TiB |
| Shared | S12    | up to 8 | 12 GiB   | 8 GiB to 1TiB |
:::

**Variable Performance** <br>
Since your cluster will be sharing vCPUs with other clusters, the performance
may vary depending on the overall load on the underlying machine. This 
variability makes it less predictable compared to Dedicated Plans, where your
database is running on dedicated resources.

**Fair-Use Principle** <br>
The Shared Plan operates on a fair-use principle. All users are expected to
utilize the shared resources responsibly so that the system remains equitable
and functional for everyone.

:::{note}
__*CRFREE__: This plan is aimed at new users who want to test and evaluate
CrateDB Cloud and is perpetually free to use. Every user can deploy one free
tier cluster in their organization without adding a payment method. Free tier
clusters will be suspended if they are not used for 7 days, and deleted after
7 more days of inactivity. They cannot be scaled or changed.
:::

##  Dedicated
CrateDB Cloud's Dedicated Plan is designed to provide robust, scalable, and
high-performance database solutions. Unlike the Shared Plan, the Dedicated Plan
offers dedicated resources, including dedicated vCPUs, to meet the demands of
high-availability and high-throughput environments.

**Node sizes**
:::{table}
:width: 700px
:widths: 200, 200, 100, 100
:align: left
| Plan | Size   | vCPUs     | RAM      |  Storage  |
|----|--------|-----------|----------| ---- |
| Dedicated | CR1    | 2  | 7 GiB    | 32 GiB  to 8 TiB |
| Dedicated | CR2    | 4  | 14 GiB   | 32 GiB  to 8 TiB |
| Dedicated | CR3    | 8  | 28 GiB   | 32 GiB  to 8 TiB |
| Dedicated | CR4    | 16  | 55 GiB   | 32 GiB  to 8 TiB |
:::


All Dedicated Plans can be scaled from 1 to 9 nodes. Depeding on the number of
nodes, the overall cluster size can be scaled up to the following limits:

**Cluster sizes**
:::{table}
:width: 700px
:widths: 200, 200, 100, 100
:align: left
| Plan | Size   | vCPUs     | RAM      |  Storage  |
|----|--------|-----------|----------| ---- |
| Dedicated | CR1    | up to 18  | up to 63 GiB    | up to 72 TiB |
| Dedicated | CR2    | up to 36  | up to 126 GiB   | up to 72 TiB |
| Dedicated | CR3    | up to 72  | up to 252 GiB   | up to 72 TiB |
| Dedicated | CR4    | up to 144  | up to 495 GiB   | up to 72 TiB |
:::

**Recommended Setup for High Availability**<br>
While it's possible to start with just one node, for applications needing high
availability and fault tolerance, we recommend using at least 3 nodes. This
ensures that your data is safely replicated and that the cluster can handle
node failures gracefully.

## Custom

For organizations with specialized requirements that go beyond the Shared and
Dedicated Plans, CrateDB Cloud offers custom solutions tailored to your
specific needs. Our sales team and solutions engineers work closely with you to
architect and deploy a custom cluster configuration, ensuring optimal
performance, scalability, and security for your mission-critical applications.

Whether you have stringent compliance mandates, complex integrations, or unique
scalability challenges, our custom solutions provide the flexibility and
expertise to meet your business objectives and technical requirements.