:orphan:
(cluster-deployment)=

# Deploy cluster

This set of tutorials explains how to subscribe and deploy your cluster on
CrateDB Cloud. The first step is always to [](#sign-up).

After you have signed up successfully, CrateDB Cloud offers two different
methods to subscribe and get started with deploying a cluster.

Quick start.

:::{card} {octicon}`table;2em` CrateDB Cloud Console
:link: https://console.cratedb.cloud/
:link-type: url

Directly navigate to the CrateDB Cloud Console.
https://console.cratedb.cloud/
:::


## Direct deployment

The easiest and recommended way to sign up for CrateDB Cloud is by using a
credit card. Payment processing for your credit card is fully PCI-compliant,
powered by [Stripe].

:::{card} Web-based deployment tutorial
:link: cluster-deployment-stripe
:link-type: ref

Deploy a CrateDB cluster using the CrateDB Cloud Web Console.
:::

:::{card} CLI deployment tutorial
:link: cluster-deployment-croud
:link-type: ref

Deploy a CrateDB cluster using the Croud command-line program.
:::


## Marketplace deployment

CrateDB Cloud also supports subscribing via Software as
a Service (SaaS) offerings on two cloud provider marketplaces,
Microsoft's Azure Marketplace and Amazon's AWS Marketplace.

:::{card} Marketplace deployment tutorials
:link: cluster-deployment-marketplace
:link-type: ref

Tutorials about the signup and deployment process for running
CrateDB clusters on Cloud provider marketplaces.
:::


[Stripe]: https://stripe.com


```{toctree}
:maxdepth: 1
:hidden:

stripe
marketplace/index
```
