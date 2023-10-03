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
- Up to 126 vCPUs
- Up to 495 GiB RAM
- Up to 72 TiB storage
- Backups (once per hour)
- Basic Support

---

- AWS / Azure Private Link
- Uptime SLAs
- Premium support available


:::

:::{grid-item-card} Enterprise
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

::::{sd-table}
:widths: 2 2 2 2 2 
:row-class: top-border

:::{sd-row}
```{sd-item} **Plan**
```
```{sd-item} **Size**
```
```{sd-item} **vCPUs**
```
```{sd-item} **RAM**
```
```{sd-item} **Storage**
```
:::

:::{sd-row}
```{sd-item} Shared
```
```{sd-item} CRFREE*
```
```{sd-item} up to 2
```
```{sd-item} 2 GiB
```
```{sd-item} 8 GiB
```
:::

:::{sd-row}
```{sd-item} Shared
```
```{sd-item} S2
```
```{sd-item} up to 2
```
```{sd-item} 2 GiB
```
```{sd-item} 8 GiB to 1 TiB
```
:::

:::{sd-row}
```{sd-item} Shared
```
```{sd-item} S4
```
```{sd-item} up to 3
```
```{sd-item} 4 GiB
```
```{sd-item} 8 GiB to 1 TiB
```
:::

:::{sd-row}
```{sd-item} Shared
```
```{sd-item} S6
```
```{sd-item} up to 4
```
```{sd-item} 6 GiB
```
```{sd-item} 8 GiB to 1 TiB
```
:::

:::{sd-row}
```{sd-item} Shared
```
```{sd-item} S8
```
```{sd-item} up to 8
```
```{sd-item} 12 GiB
```
```{sd-item} 8 GiB to 1 TiB
```
:::

::::

**Variable Performance** <br>
Since your cluster will be sharing vCPUs with other clusters, the performance
may vary depending on the overall load on the underlying machine. This 
variability makes it less predictable compared to Dedicated Plans, where you
have dedicated resources.

**Fair-Use Principle** <br>
The Shared Plan operates on a fair-use principle. All users are expected to use
the shared resources responsibly so that the system remains equitable and
functional for everyone.

:::{note}
__*CRFREE__: This plan is aimed at new users who want to test and evaluate
CrateDB Cloud, and is perpetually free to use. Users can deploy one free
tier cluster in their organization without needing to add a payment method. Free tier
clusters will be suspended if they are not used for 7 days, and deleted after
7 more days of idleness. They cannot be scaled or changed.
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
| Dedicated | CR1    | 1.75  | 7 GiB    | 8 GiB  to 8 TiB |
| Dedicated | CR2    | 3.5  | 14 GiB   | 8 GiB  to 8 TiB |
| Dedicated | CR3    | 7  | 28 GiB   | 8 GiB  to 8 TiB |
| Dedicated | CR4    | 14  | 55 GiB   | 8 GiB  to 8 TiB |
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
| Dedicated | CR1    | up to 15.75  | up to 63 GiB    | up to 72 TiB |
| Dedicated | CR2    | up to 31.5  | up to 126 GiB   | up to 72 TiB |
| Dedicated | CR3    | up to 63  | up to 252 GiB   | up to 72 TiB |
| Dedicated | CR4    | up to 126  | up to 495 GiB   | up to 72 TiB |
:::

**Recommended Setup for High Availability**<br>
While it's possible to start with just one node, for applications requiring high
availability and fault tolerance, we recommend using at least 3 nodes. This
ensures that your data is safely replicated and that the cluster can handle
node failures gracefully.

## Enterprise

For organizations with specialized requirements that go beyond our Shared and
Dedicated Plans, CrateDB Cloud offers Enterprise solutions tailored to your
specific needs. Our sales team and solutions engineers work closely with you to
architect and deploy a custom cluster configuration, ensuring optimal
performance, scalability, and security for your mission-critical applications.
Whether you have stringent compliance mandates, complex integrations, or unique
scalability challenges, our Enterprise solutions provide the flexibility and
expertise to meet your business objectives.