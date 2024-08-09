(cluster-backups)=
# Backups 

You can find the Backups page in the detailed view of your cluster and
you can see and restore all existing backups here.

By default, a backup is made every hour. The backups are kept for 14
days. We also keep the last 14 backups indefinitely, no matter the state
of your cluster.

The Backups tab provides a list of all your backups. By default, a
backup is made every hour.

![Cloud Console cluster backups page](../_assets/img/cluster-backups.png)

You can also control the schedule of your backups by clicking the *Edit
backup schedule* button.

![Cloud Console cluster backups edit page](../_assets/img/cluster-backups-edit.png)

Here you can create a custom schedule by selecting any number of hour
slots. Backups will be created at selected times. At least one backup a
day is mandatory.

To restore a particular backup, click the *Restore* button. A popup
window with a SQL statement will appear. Input this statement to your
Admin UI console either by copy-pasting it, or clicking the *Run query
in Admin UI*. The latter will bring you directly to the Admin UI console
with the statement automatically pre-filled.

![Cloud Console cluster backups restore page](../_assets/img/cluster-backups-restore.png)

You have a choice between restoring the cluster fully, or only specific
tables.

(cluster-cloning)=
## Cluster Cloning 

Cluster cloning is a process of duplicating all the data from a specific
snapshot into a different cluster. Creating the new cluster isn't part
of the cloning process, you need to create the target cluster yourself.
You can clone a cluster from the Backups page.

![Cloud Console cluster backup snapshots](../_assets/img/cluster-backups.png)

Choose a snapshot and click the *Clone* button. As with restoring a
backup, you can choose between cloning the whole cluster, or only
specific tables.

![Cloud Console cluster clone popup](../_assets/img/cluster-clone-popup.png)

:::{note}
Keep in mind that the full cluster clone will include users, views,
privileges and everything else. Cloning also doesn't distinguish
between cluster plans, meaning you can clone from CR2 to CR1 or any
other variation.
:::

(cluster-cloning-fail)=
## Failed cloning 

There are circumstances under which cloning can fail or behave
unexpectedly. These are:

-   If you already have tables with the same names in the target cluster
    as in the source snapshot, the entire clone operation will fail.
-   There isn't enough storage left on the target cluster to
    accommodate the tables you're trying to clone. In this case, you
    might get an incomplete cloning as the cluster will run out of
    storage.
-   You're trying to clone an invalid or no longer existing snapshot.
    This can happen if you're cloning through
    [Croud](https://cratedb.com/docs/cloud/cli/en/latest/). In this case,
    the cloning will fail.
-   You're trying to restore a table that is not included in the
    snapshot. This can happen if you're restoring snapshots through
    [Croud](https://cratedb.com/docs/cloud/cli/en/latest/). In this case,
    the cloning will fail.

When cloning fails, it is indicated by a banner in the cluster overview
screen.

![Cloud Console cluster failed cloning](../_assets/img/cluster-clone-failed.png)
