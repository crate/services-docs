(reconfigure-cluster)=
# Scale cluster

Scaling or reconfiguring your cluster happens on the \"Scale\" tab of
the CrateDB Cloud Console. The page displays the current configuration of your 
cluster. You can see your current plan, the resources of a single node, and the
overall resources of the cluster.

![Cloud Console cluster scaling tab](../_assets/img/cluster-scale.png)

You can scale your cluster by selecting a different configuration and
then clicking the **"Scale cluster"** button on the right.

Now you can do three different things:

-   Change the compute plan of your cluster
-   Increase storage on each node
-   Increase/decrease the number of nodes

You can do only one of those operations at a time, i.e., you can\'t
change plans and scale the number of nodes at the same time.

The difference in the price of the cluster can be seen on the right, when
choosing different configurations.

:::{caution}
Storage capacity increases for a cluster are permanent and cannot be reversed.
To decrease storage capacity, you can either reduce the number of cluster nodes
(minimum of 2 nodes, though we recommend at least 3 for production environments)
or start a new cluster with a smaller storage configuration and restore a backup
to it.
:::
