.. _subscription-plans:

==================
Subscription Plans
==================

When signing up for the CrateDB Cloud service, you have a choice of
different subscription plans. Each plan is preconfigured for different use cases, depending on your storage and computation needs. At the same
time, the plans also offer elasticity, to accompany use case changes.

Within certain plans, you can horizontally scale the capacity of your
cluster up or down by adding or subtracting nodes. Limited vertical scaling is
also possible with storage scaling (up only). For more information on how to
do this, please refer to the `scaling guide`_.

This documentation section first explains the plans for the recommended
subscription method, `subscribing and deploying a cluster directly`_.
Subsequently, we will provide some more detailed information regarding
plans and billing options based on the Marketplace SaaS offerings.

.. rubric:: Table of contents

.. contents::
   :local:


.. _subscription-plans-stripe:

Overview
========

The standard CrateDB Cloud offer consists of three products: *Free*, *Shared*,
and *Dedicated*

Each product/plan has two dimensions: compute and storage.

:Compute:

    The compute configuration is pre-defined for each plan, and can be scaled
    horizontally by adding or removing database nodes, during or after deployment.

:Storage:

    Storage is configured separately. On deployment, you can set the desired 
    storage capacity for your cluster, within the range of storage capacity
    options provided for that plan. Storage can be scaled up but cannot be scaled down afterward.

.. seealso::

    To view the current plans, prices, compute and storage ranges, refer to the
    `pricing page`_.

    For details on signup, cluster configuration, and cluster deployment, 
    please see the `deployment tutorial`_.

.. note::

    Although you can scale your cluster from a single node to as many nodes as
    desired, only clusters containing 3 or more nodes are covered by the 24/7
    support. You can find the CrateDB Cloud terms and conditions in the `SLA`_.

.. note::

    `CrateDB Edge`_ works differently. Since it allows hosting CrateDB Cloud
    on your local or self-service Kubernetes stack, there is no need for
    different subscription plans. You can combine CrateDB Edge with any
    suitable hardware configuration that works for your use case.

.. _crfree:

Free
-----

This plan, also known as CRFREE, is aimed at new users for testing and 
evaluation of CrateDB Cloud. It is perpetually free to use. Every user can 
deploy one free tier cluster in their organization without adding a payment
method. This plan also doesn't consume 
any :ref:`Free Credit <free-trial-budget>` that you may have available.

The cluster resources are limited to one node with up to 2 CPUs, 2 GiB of 
memory, and 8 GiB of storage, which is suitable for basic evaluation purposes.
This plan doesn't offer any kind of scaling.

The CRFREE plan is designed for active testing and evaluation. Clusters under 
this plan are suspended after 7 days of inactivity. After another 7 days, the
cluster is automatically deleted if left suspended.

.. _shared:

Shared
------

Shared-resource plans are used to deploy clusters that allow for better 
resource utilization. These clusters share compute and storage resources
with other clusters in this category. Because of this, they offer a more
cost-effective solution for smaller teams and experimental deployments of
low-traffic applications. They are limited to one node with up to 8 CPUs, 12 
GiB of memory, and 1 TiB of storage. 

The vCPU displayed for each tier is an 'up to' value and is not guaranteed.
Memory and storage are guaranteed. Scaling within the Shared tier is supported.
You can scale from S2 to S12 and vice versa. It is also possible to upgrade
from Shared plans to Dedicated plans, but not the other way around. Snapshots
in this tier are limited to once per day and are kept for 14 days.

+------------+--------------+-----------+
| Size/Name  | CPU          | Memory    |
+============+==============+===========+
| S2         | Up to 2 vCPU | 2 GiB     |
+------------+--------------+-----------+
| S4         | Up to 3 vCPU | 4 GiB     |
+------------+--------------+-----------+
| S6         | Up to 4 vCPU | 6 GiB     |
+------------+--------------+-----------+
| S12        | Up to 8 vCPU | 12 GiB    |
+------------+--------------+-----------+

.. _dedicated:

Dedicated
---------

These are the base plans that offer the best performance and the biggest
flexibility. Their specs start from 1.75 CPU, 7 GiB RAM, and 32GiB storage all
the way to 14 CPU, 55 GiB RAM, and 8 TiB storage per-node. These plans can be 
scaled up to a maximum of 9 nodes. If you need more nodes than this, feel free 
to `contact us`_ at any time.

.. WARNING::

    An even number of nodes can be used for testing and development without
    issue, but is not recommended for production workloads due to the risk of
    `split-brain syndrome`_.

.. _subscription-plans-regions:

Regions
=======

The subscriptions are currently offered in three :ref:`regions <gloss-region>`:
One from AWS (West Europe) and two from Azure (East US 2 and West Europe). You
can use any subscription plan in any region. Note that prices for a given plan
differ depending on the region you select. We also accept region requests, in
case your preferred region is not currently available.

.. _subscription-plans-tiers:

Marketplace Offer
=================

If you have an existing Azure/AWS marketplace account and want to subscribe to
CrateDB Cloud using that, you can. The principles are the same as with credit
card subscription, which allows maximum flexibility regarding deployment and
scaling up/down:

- Usage is billed based on consumption
- Billing is done in $0.001 increments for the compute + storage usage

For details visit :ref:`Azure <signup-azure-to-cluster>`, or :ref:`AWS
<signup-aws-to-cluster>` marketplace deployment tutorials.

.. _subscription-plans-contracts:

CrateDB Cloud Contract
======================

The **CrateDB Cloud Contract** allows you to pay for a full year's worth of 
the service of your choice in advance. Depending on the specifics of the 
contract chosen, it may be possible to negotiate a discount based on the up
front payment. The CrateDB Cloud Contract is only available via supported
cloud providers on the SaaS Marketplaces. For more information, contact the
`Sales team`_.

.. _AWS Marketplace: https://aws.amazon.com/marketplace/pp/B089M4B1ND
.. _AWS subscription page: https://aws.amazon.com/marketplace/pp/B089M4B1ND
.. _Azure Marketplace: https://azuremarketplace.microsoft.com/en-us/marketplace/apps/crate.cratedbcloud?tab=PlansAndPrice
.. _Azure offer page: https://azuremarketplace.microsoft.com/en-us/marketplace/apps/crate.cratedbcloud?tab=Overview
.. _contact us: sales@crate.io
.. _Contract page on the AWS Marketplace: https://aws.amazon.com/marketplace/pp/B08KHK34RK
.. _CrateDB Edge: https://crate.io/products/cratedb-edge/
.. _deployment tutorial: https://crate.io/docs/cloud/tutorials/en/latest/cluster-deployment/stripe.html
.. _pricing page: https://crate.io/pricing
.. _Sales department: sales@crate.io
.. _Sales team: sales@crate.io
.. _scale your cluster: https://crate.io/docs/cloud/howtos/en/latest/reconfigure-cluster.html
.. _scaling guide: https://crate.io/docs/cloud/howtos/en/latest/reconfigure-cluster.html
.. _SLA: https://crate.io/legal/service-level-agreement
.. _split-brain syndrome: https://en.wikipedia.org/wiki/Split-brain_(computing)
.. _subscribing and deploying a cluster directly: https://crate.io/docs/cloud/tutorials/en/latest/cluster-deployment/stripe.html