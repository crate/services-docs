
(cluster-manage)=
# Manage Cluster 

The manage tab contains credentials settings, deletion protection,
upgrades, IP allowlist, private links, suspend cluster, and delete
cluster options.

![Cloud Console Manage tab](../_assets/img/cluster-manage.png)

## Credentials

These are the username and password used for accessing the Admin UI of your
cluster. Username is always admin and the password can be changed.

## Deletion protection
While this is enabled, your cluster cannot be deleted.

## Upgrade CrateDB
Here you can enable the CrateDB version running on your cluster.

## IP Allowlist
By using the IP allowlisting feature, you can restrict access to your cluster to
an indicated IP address or [CIDR block](https://www.keycdn.com/support/what-is-cidr). Click the blue *Add Address* button and you can fill out an IP address or range
and give it a meaningful description. Click *Save* to store it or the bin icon
to delete a range. Keep in mind that once IP allowlisting has been set, you
cannot access the Admin UI for that cluster from any other address.

If no allowlist address or address range is set, the cluster is publicly
accessible by default. (Of course, the normal authentication procedures are
always required.) Only an {ref}`org admin <org-roles>` can change the allowlist.

## Private links
A private endpoint, or private link, is a mechanism that allows a secure, private connection to your cluster. Effectively, it allows you to bypass the public internet when accessing the environment where your cluster is deployed. Note that private endpoints don't work across providers, meaning that if you want to securely access your AWS cluster, you must do so from within the AWS environment.

## Suspend cluster
Cluster suspension is a feature that enables you to temporarily pause your cluster while retaining all its data. An example situation might be that the project you're working on has been put on hold. The cost of running a cluster is split into two
parts: Compute and Storage. The benefit here is that while the cluster is suspended, you are only charged for the storage.

## Delete cluster
All cluster data will be lost on deletion. This action cannot be undone.