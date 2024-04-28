(cloud-on-kubernetes)=
# CrateDB Cloud on Kubernetes

**CrateDB Cloud on Kubernetes** is the hybrid cloud database solution 
integrating CrateDB clusters and the CrateDB Cloud software stack with
on-premise or customer-controlled cloud infrastructure.

## Introduction

The CrateDB Cloud on Kubernetes concept is simple. You bring your own 
Kubernetes infrastructure - whether in a production site, office, laboratory,
or local setup, or in your existing managed cloud infrastructure on AWS,
Azure, or GCP.

Wherever it may be located, we provide the full experience of CrateDB
Cloud to that Kubernetes environment. You keep your existing
infrastructure setup and you get all the benefits of CrateDB Cloud on
top: from quick deployment to seamless scaling and easy cluster
management.

(cloud-on-kubernetes-details)=
## Details

The process of getting CrateDB Cloud on Kubernetes running is 
supported by the CrateDB Cloud Console.

Even so, there are some steps involved, and some requirements have to be
met in order for it to work. This section of the documentation intends
to serve as an end-to-end walkthrough of the corresponding process and
prerequisites.

(cloud-on-kubernetes-tutorials)=
## Tutorials

In these tutorials, we first introduce the signup and configuration
process for a local Kubernetes installation. Next, we explain the
process end-to-end for using AKS and EKS services. After that, we
outline the installation method for some lightweight Kubernetes
distributions, like K3s and Microk8s.

Then, we explain how to set up a custom backup location, so you can keep
full ownership of your data backups.

We also introduce a way to monitor your CrateDB Cloud on Kubernetes cluster
in the visualization tool Grafana coupled with Loki and Prometheus.

::::{grid} 2 2 2 3
:margin: 4 4 0 0
:gutter: 1

:::{grid-item-card} {octicon}`info` Introduction
:link: edge-disclaimer
:link-type: ref
Find about about hardware and software prerequisites for 
running CrateDB Cloud on Kubernetes.
:::

:::{grid-item-card} {octicon}`people` Managed Kubernetes
:link: edge-providers
:link-type: ref
In this section, we provide more specific installation instructions 
for some managed Kubernetes providers.
:::

:::{grid-item-card} {octicon}`person` Self-hosted Kubernetes
:link: edge-self-hosted
:link-type: ref
In this section, we outline installation instructions for some 
third-party supported self-hosted options.
:::

:::{grid-item-card} {octicon}`package-dependencies` Custom backup location
:link: edge-custom-backup
:link-type: ref
This guide introduces a feature of CrateDB Cloud on Kubernetes 
that lets users specify their backup location.
:::

:::{grid-item-card} {octicon}`pulse` Monitoring
:link: edge-monitoring
:link-type: ref
Learn how to monitor CrateDB Cloud on Kubernetes using Prometheus,
Loki, and Grafana.
:::

::::

:::{toctree}
:hidden:
:maxdepth: 1

Introduction <introduction>
Managed Kubernetes options <managed-kubernetes>
Self-hosted Kubernetes <self-hosted-edge>
Custom backup location <custom-backup>
Monitor CrateDB Cloud on Kubernetes <monitoring>
:::
