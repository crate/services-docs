.. _console-overview:

=====================
CrateDB Cloud Console
=====================

The **CrateDB Cloud Console** is a hosted web administration interface for
interacting with `CrateDB Cloud`_.

.. note::

    Refer to individual items in the current section of the documentation for more
    information on how to perform specific operations. You can also refer to the
    :ref:`glossary <glossary>` for more information on CrateDB Cloud-related terminology.

.. rubric:: Table of contents

.. contents::
   :local:

.. _overview-basics:

Basics
======

.. image:: ../_assets/img/start.png
   :alt: CrateDB Cloud sign-in screen

The CrateDB Cloud user interface permalink is the `CrateDB Cloud Console`_.
You can `deploy a trial cluster on the CrateDB Cloud Console for free`_.

Here is a list of all currently available regions for CrateDB Cloud:

+-------------------+----------------------------------------+
| Region            | URL                                    |
+===================+========================================+
| AWS West Europe   | `eks1.eu-west-1.aws.cratedb.cloud`_    |
+-------------------+----------------------------------------+
| Azure East-US2    | `aks1.eastus2.azure.cratedb.cloud`_    |
+-------------------+----------------------------------------+
| Azure West Europe | `aks1.westeurope.azure.cratedb.cloud`_ |
+-------------------+----------------------------------------+

Azure East-US2 and Azure West-Europe are managed by `Microsoft Azure`_. The
AWS region is managed by AWS and is located in Ireland. Note that the AWS
region does not serve the CrateDB Cloud Console directly.

From the Cloud Console homepage, you can sign in using a Github, Google, or
Microsoft Azure account or by creating a separate username and password.

If you don't have a Cloud Console account yet, follow the steps in the `signup
tutorial`_. Select the authentication method you wish to use. From there, you
will be given the option to sign up.

Once signed in, you will be presented with the Organization overview.


.. _overview-org-overview:

Organization
============

The organization is the highest structure in your CrateDB Cloud Console.
Multiple clusters and users can exist in a organization at any moment. For 
first-time users, an organization called "My organization" is automatically 
created upon first login.

To see a list of all the organizations you have acesss to, go to 

the My Account page in the dropdown menu in the top-right.

.. image:: ../_assets/img/organization-dashboard.png
   :alt: Cloud Console organization overview

The Organization overview consists of six tabs: *Clusters*, *Settings*, 
*Billing*, *Payment Methods*, *Audit Logs*, and *Regions*. By default
you are brought to the Clusters tab, which provides a quick overview of all
your clusters.

.. image:: ../_assets/img/clusters-overview.png
   :alt: Cloud Console clusters overview

If you are a member of multiple organizations, you can quickly change
between them on every tab/page in the Cloud Console. Simply use the
dropdown menu at the top-right of the current page/tab: 

.. image:: ../_assets/img/change-organization.png
   :alt: Cloud Console quick org swap

The CrateDB Cloud Console is structured on a per-organization basis: all pages
and tabs in the Console will display values for the currently selected
organization.


.. _overview-general-settings:

Settings
--------

The Settings tab shows you the name, notification settings, and ID of your
currently selected organization.

.. image:: ../_assets/img/general-settings.png
   :alt: Cloud Console general settings tab

By clicking the *Edit* button next to the organization, you can rename it. 
Here you can also set the email address for notifications and indicate whether
you want to receive them or not.

It also shows a list of users in your organization. You can add new users by
clicking the "Add user" button. You can also choose the role of a new user. 
To learn more about user roles and their meaning, see the documentation
on `user roles`_.

.. _overview-org-billing:

Organization Billing
--------------------

The Billing tab shows all your existing subscriptions, along with which
cluster is currently using the subscription. The current accumulated billing
snapshot is also visible here, along with additional information:

.. image:: ../_assets/img/billing-meter.png
   :alt: Cloud Console billing meter

.. NOTE::
    Subscriptions cannot be deleted in the billing tab. To delete a
    subscription, please contact support.

.. _overview-org-payment-methods:

Organization payment methods
----------------------------

This tab shows all the information about your payment methods. If you have
signed up with a credit card for your cluster (the recommended route), your
card information overview will be shown here.

In case you use multiple cards, a default card can be set and cards can be
deleted from the list by using the dots icon to the right of the card listing.
Click the *Add payment method* button at the top right to add a new card.

Cloud subscription payment methods can also be added here.

.. image:: ../_assets/img/payment-methods2.png
   :alt: Cloud Console payment methods

.. _overview-org-audit:

Organization Audit Logs
-----------------------

This tab shows the Audit Logs of the current organization.

.. image:: ../_assets/img/organization-audit-log.png
   :alt: Cloud Console organization audit log tab

In the Audit Log, a user with the correct credentials (`an organization
admin`_) can see an overview of logged changes to the organization.

.. _overview-org-regions:

Organization Regions
--------------------

In this tab, you will see the available :ref:`regions <gloss-region>` for
cluster deployment. It is possible to deploy clusters on this screen as well,
by clicking the *Deploy cluster* button under each respective region field.

For those with access to `CrateDB Edge`_, this tab also allows the deployment
of :ref:`CrateDB Edge <gloss-edge>` clusters in a :ref:`custom region
<gloss-region>`. To do so, provide a name for the custom region and click the
*Create edge region* button. Once created, the custom region will appear:

.. image:: ../_assets/img/organization-regions.png
   :alt: Cloud Console organization regions tab

This field will show a script to set up the dependencies for cluster
deployment in the custom region. Apply the script in your local CLI and follow
the prompts to proceed. A ``--help`` parameter is available within the script
for further information.

.. _overview-cluster:

Cluster
=======

The detailed view of Cluster provides a broad range of relevant data of the
selected cluster. It also displays metrics for the cluster. It can be accessed
by clicking "View" on the desired cluster in the Clusters tab.

.. image:: ../_assets/img/cluster-overview.png
   :alt: Cloud Console cluster overview page

Information visible on the Overview page includes:

.. _overview-cluster-overview:

Overview
--------

* **Status**: Current status of your cluster:
   
- GREEN: Your cluster is healthy.
- YELLOW: Some of your tables have under-replicated shards. Please log in
  to your cluster's Admin UI to check.
- RED: Some of your tables have missing shards. This can happen if you've
  recently restarted a node. The support team is already notified and
  investigating the issue.

* **Region**: Name of the region where the cluster is deployed.

* **Plan**: This shows which :ref:`subscription plan <subscription-plans>` the
  cluster is running on.

* **CPU metrics**: Average CPU utilization on average per node. The sparkline shows the trend for the last hour.

* **Number of nodes**: Number of nodes in the cluster.

* **RAM metric**: Percentage of ram used in each node on average. The sparkline shows the trend for the last hour.

* **Storage metrics**: Used and overall storage of the cluster. The sparkline shows the trend for the last hour.

* **Version**: This indicates the version number of CrateDB the cluster is
  running.

* **Query metric**: Queries per second.

.. _overview-cluster-overview-admin-ui:

Admin UI
~~~~~~~~

* **Access cluster**: The *Open Admin UI* button connects you to
  the `CrateDB Admin UI`_ for the cluster at its unique URL.

.. NOTE::

    The Cluster URL points to a load balancer that distributes traffic
    internally to the whole CrateDB cluster. The load balancer closes idle
    connections after four minutes, therefore client applications that require
    stateful connections (e.g., JDBC) must be configured to send keep-alive
    heartbeat queries.

.. _overview-cluster-overview-next-steps:

Next Steps
~~~~~~~~~~

* **Import Data**: Import some data into your cluster using the data import
  tool.

* **See my backups**: The "see my backups" will take you to the Backups tab, where 
  you can see all your backups. CrateDB Cloud clusters can now be cloned to a new 
  cluster from any backup.

* **API endpoint**: CrateDB Cloud provides a Prometheus-compatible API 
  endpoint for cluster metrics.

For more information on the CrateDB concepts used here, refer to the `CrateDB
architecture documentation`_ or the :ref:`glossary <glossary>`.

.. _overview-connect-to-your-cluster:

Connecting to your cluster
~~~~~~~~~~~~~~~~~~~~~~~~~~

Here you can see a list of snippets for the available clients and libraries. 
These include: CLI, Python, Ruby, Java, JavaScript, PHP.

.. _overview-import-tab:

Import
------

.. image:: ../_assets/img/cluster-import-tab.png
   :alt: Cloud Console cluster import tab

The first thing you see in the "Import" tab is the history of your imports. 
You can see whether you imported from a URL or from a file, file name, table
into which you imported, date, and status. By clicking "Show details" you can
display details of a particular import.

Clicking the "Import new data" button will bring up the Import page, where you
can select the source of your data. 

If you don't have a dataset prepared, we also provide an example in the URL
import section. It's the New York City taxi trip dataset for July of 2019 
(about 6.3M records).

.. _overview-cluster-import-url:

Import from URL
~~~~~~~~~~~~~~~

To import data, fill out the URL, name of the table which will be created and
populated with your data, data format, and whether it is compressed.

If a table with the chosen name doesn’t exist, it will be automatically 
created. 

The following data formats are supported:

- CSV (all variants)
- JSON (JSON-Lines, JSON Arrays and JSON Documents)
- Parquet

Gzip compressed files are also supported.

.. image:: ../_assets/img/cluster-import-tab-url.png
   :alt: Cloud Console cluster upload from URL

.. _overview-cluster-import-s3:

Import from private S3 bucket
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

CrateDB Cloud allows convenient imports directly from S3-compatible storage. 
To import a file form bucket, provide the name of your bucket, and path to
the file. The S3 Access Key ID, and S3 Secret Access Key are also needed. You 
can also specify the endpoint for non-AWS S3 buckets. Keep in mind that you may
be charged for egress traffic, depending on your provider. There is also a
volume limit of 10 GiB per file for S3 imports. The usual file formats are
supported - CSV (all variants), JSON (JSON-Lines, JSON Arrays and JSON Documents), and Parquet.

.. image:: ../_assets/img/cluster-import-tab-s3.png
   :alt: Cloud Console cluster upload from S3

.. NOTE::

   It's important to make sure that you have the right permissions to access objects in the specified bucket. For AWS S3, your user should have a policy that allows GetObject access, for example:

      .. code-block:: console

       {
        "Version": "2012-10-17",
        "Statement": [
        {
            "Sid": "AllowGetObject",
            "Effect": "Allow",
            "Principal": {
                "AWS": "*"
            },
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::EXAMPLE-BUCKET-NAME/*"
        }]
        }

.. _overview-cluster-import-azure:

Import from Azure Blob Storage Container
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Importing data from private Azure Blob Storage containers is possible using a stored secret, which includes a secret name and either an Azure Storage Connection string or an Azure SAS Token URL. An admin user at the organization level can add this secret.

You can specify a secret, a container, a table and a path in the form
`/folder/my_file.parquet` 

As with other imports Parquet, CSV, and JSON files are supported. File size
limitation for imports is 10 GiB per file.

.. image:: ../_assets/img/cluster-import-tab-azure.png
   :alt: Cloud Console cluster upload from Azure Storage Container

.. _overview-cluster-import-globbing:

Importing multiple files
~~~~~~~~~~~~~~~~~~~~~~~~

Importing multiple files, also known as import globbing is supported in any
s3-complatible blob storage. The steps are the same as if importing from S3,
i.e. bucket name, path to the file and S3 ID/Secret.

Importing multiple files from Azure Container/Blob Storage is also supported:
`/folder/*.parquet`

Files to be imported are specified by using the well-known `wildcard`_
notation, also known as "globbing". In computer programming, `glob`_ patterns
specify sets of filenames with wildcard characters. The following example would
import all the files from the single specified day.

.. code-block:: console
  
  /somepath/AWSLogs/123456678899/CloudTrail/us-east-1/2023/11/12/*.json.gz

.. image:: ../_assets/img/cluster-import-globbing.png
   :alt: Cloud Console cluster import globbing

As with other imports, the supported file types are CSV, JSON,
and Parquet.

.. _overview-cluster-import-file:

Import from file
~~~~~~~~~~~~~~~~

Uploading directly from your computer offers more control over your data.
From the security point of view, you don’t have to share the data on the 
internet just to be able to import it to your cluster. You also have more 
control over who has access to your data. Your files are temporarily uploaded
to a secure location managed by Crate (an S3 bucket in AWS) which is not
publicly accessible. The files are automatically deleted after 3 days. 
You may re-import the same file into multiple tables without having to
re-upload it within those 3 days. Up to 5 files may be uploaded at the same
time, with the oldest ones being automatically deleted if you upload more.

.. image:: ../_assets/img/cluster-import-tab-file.png
   :alt: Cloud Console cluster upload from file

As with other import, the supported file formats are:

- CSV (all variants)
- JSON (JSON-Lines, JSON Arrays and JSON Documents)
- Parquet 

There is also a limit to file size, currently 1GB.

.. _overview-cluster-import-schema-evolution:

Schema evolution
~~~~~~~~~~~~~~~~

A feature called Schema Evolution is offered for all the different import
types. When enabled, new columns can automatically be added to your existing
tables when importing data. This feature helps eliminate the need for
pre-defining the table schemas. This applies to both existing tables, and those
created by import job. It can be enabled/disabled by "Schema evolution"
checkbox on the import page.

.. _overview-cluster-import-limitations:

Import Limitations
~~~~~~~~~~~~~~~~~~

**CSV** files:

1. Comma, tab and pipe delimiters are supported.

**JSON** files:

The following formats are supported for JSON:

1. JSON Documents. Will insert as a single row in the table.

   .. code-block:: console

       {
         "id":1,
         "text": "example"
       }

2. JSON Arrays. Will insert as a row per array item.

   .. code-block:: console

      [
        {
          "id":1,
          "text": "example"
        },
        {
          "id":2,
          "text": "example2"
        }
      ]

3. JSON-Lines. Each line will insert as a row.

   .. code-block:: console

      {"id":1, "text": "example"}
      {"id":2, "text": "example2"}

4. Schema evolution only adds new columns, it does not modify existing ones.
   This means that if you have a column "OrderID" of type `INTEGER` in your
   existing table and you try to import data, with Schema Evolution turned on,
   where there is a "OrderID" column of type `STRING`, the import job will fail.

.. _overview-cluster-export:

Export
------

The export tab allows users to download specific tables/views. When you first
visit the Export tab, you can specify the name of a table/view, format (CSV,
JSON, or Parquet) and whether you'd like your data to be gzip compressed 
(recommended for CSV and JSON files).

.. NOTE::

   Parquet is a highly compressed data format for very efficient storage of
   tabular data. Please note that for OBJECT and ARRAY columns in CrateDB, the
   exported data will be JSON encoded when saving to Parquet (effectively saving them
   as strings). This is due to the complexity of encoding structs and lists
   in the Parquet format, where determining the exact schema might not be possible.
   When re-importing such a Parquet file, make sure you pre-create the table with the
   correct schema.


.. image:: ../_assets/img/cluster-export.png
   :alt: Cloud Console cluster export tab

History of your exports is also visible in the Export tab.

.. image:: ../_assets/img/cluster-export-tab-history.png
   :alt: Cloud Console cluster export tab history

.. NOTE::

   Export limitations:

   - Size limit for exporting is 1 GiB
   - Exports are held for 3 days, then automatically deleted

.. _overview-cluster-backups:

Backups
-------

You can find the Backups page in the detailed view of your cluster and you can
see and restore all existing backups here. 

By default, a backup is made every hour. The backups are kept for 14 days.
We also keep the last 14 backups indefinitely, no matter the state of your cluster.

The Backups tab provides a list of all your backups. By default, a backup is
made every hour.

.. image:: ../_assets/img/cluster-backups.png
   :alt: Cloud Console cluster backups page

You can also control the schedule of your backups by clicking the *Edit backup
schedule* button.

.. image:: ../_assets/img/cluster-backups-edit.png
   :alt: Cloud Console cluster backups edit page

Here you can create a custom schedule by selecting any number of hour slots.
Backups will be created at selected times. At least one backup a day is
mandatory.

To restore a particular backup, click the *Restore* button. A popup window
with a SQL statement will appear. Input this statement to your Admin UI
console eitheir by copy-pasting it, or clicking the *Run query in Admin UI*.
The latter will bring you directly to the Admin UI console with the statement
automatically pre-filled.

.. image:: ../_assets/img/cluster-backups-restore.png
   :alt: Cloud Console cluster backups restore page

You have a choice between restoring the cluster fully, or only specific 
tables. 

.. _overview-cluster-cloning:

Cluster Cloning
~~~~~~~~~~~~~~~

Cluster cloning is a process of duplicating all the data from a
specific snapshot into a different cluster. Creating the new cluster isn't
part of the cloning process, you need to create the target cluster yourself. 
You can clone a cluster from the Backups page. 

.. image:: ../_assets/img/cluster-backups.png
   :alt: Cloud Console cluster backup snapshots

Choose a snapshot and click the *Clone* button. As with restoring a backup, 
you can choose between cloning the whole cluster, or only specific tables.

.. image:: ../_assets/img/cluster-clone-popup.png
   :alt: Cloud Console cluster clone popup

.. NOTE::

    Keep in mind that the full cluster clone will include users, views,
    privileges and everything else. Cloning also doesn't distinguish between 
    cluster plans, meaning you can clone from CR2 to CR1 or any other
    variation.

.. _overview-cluster-cloning-fail:

Failed cloning
~~~~~~~~~~~~~~

There are circumstances under which cloning can fail or behave unexpectedly.
These are:

* If you already have tables with the same names in the target cluster
  as in the source snapshot, the entire clone operation will fail.

* There isn't enough storage left on the target cluster to accommodate the
  tables you're trying to clone. In this case, you might get an incomplete
  cloning as the cluster will run out of storage.

* You're trying to clone an invalid or no longer existing snapshot. This can
  happen if you're cloning through `Croud`_. In this case, the cloning will
  fail.

* You're trying to restore a table that is not included in the snapshot. This
  can happen if you're restoring snapshots through `Croud`_. In this case, 
  the cloning will fail.

When cloning fails, it is indicated by a banner in the cluster overview
screen.

.. image:: ../_assets/img/cluster-clone-failed.png
   :alt: Cloud Console cluster failed cloning

.. _overview-cluster-settings-scale:

Scale
-----

In the Scale tab, current configuration of your cluster is shown. You can see
your current plan, resources of a single node, and overall resources of the
cluster.

.. image:: ../_assets/img/cluster-scale.png
   :alt: Cloud Console cluster scaling tab

You can scale your cluster by clicking the *Edit cluster configuration* button
in the top-right:

.. image:: ../_assets/img/cluster-scale-edit.png
   :alt: Cloud Console cluster scaling edit

Now you can do three different things:

- Change the plan of your cluster
- Increase storage on each node
- Icrease/decrease the number of nodes

You can do only one of those operations at a time, i.e. you can't change plans
and scale the number of nodes at the same time.

The difference in price of the cluster can be seen on the bottom right, when
choosing different configurations.

.. NOTE::

    Any promotions or discounts applicable to your cluster will be applied for
    your organization as a whole at the end of the billing period. Due to
    technical limitations, they may not be directly visible in the cluster
    scale pricing shown here, but do not worry! This does not mean that your
    promotion or discount is not functioning.

.. WARNING::

    Storage capacity increases for a given cluster are irreversible. To reduce
    cluster storage capacity, reduce the cluster nodes instead (up to a
    minimum of 2, although we recommend maintaining a minimum of 3 for
    production use).

.. _overview-cluster-manage:

Manage
------

The manage tab contains credentials settings, deletion protection, upgrades, 
IP allowlist, private links, suspend cluster, and delete cluster options.

.. image:: ../_assets/img/cluster-manage.png
   :alt: Cloud Console Manage tab

* **Credentials** - These are the username and password used for accessing the
  Admin UI of your cluster. Username is always admin and the password can be
  changed.

* **Deletion protection** - While this is enabled, your cluster cannot be
  deleted.

* **Upgrade CrateDB** - Here you can enable the CrateDB version running on
  your cluster.

* **IP Allowlist** - By using the IP allowlisting feature, you can restrict 
  access to your cluster to an indicated IP address or `CIDR block`_. Click 
  the blue *Add Address* button and you can fill out an IP address or range 
  and give it a meaningful description. Click *Save* to store it or the bin
  icon to  delete a range. Keep in mind that once IP allowlisting has been 
  set, you cannot access the Admin UI for that cluster from any other address.

  If no allowlist address or address range is set, the cluster is publicly
  accessible by default. (Of course, the normal authentication procedures are
  always required.) Only an :ref:`org admin <org-roles>` can change the
  allowlist.

* **Private links** - A private endpoint, or private link, is a mechanism 
  that allows a secure,  private connection to your cluster. Effectively, it
  allows you to bypass the public internet when accessing the environment 
  where your cluster is deployed. Note that private endpoints don't work
  accross providers, meaning that if you want to securely access your AWS
  cluster, you must do so from within the AWS environment.

* **Suspend cluster**
  Cluster suspension is a feature that enables you to temporarily pause your 
  cluster while retaining all its data. An example situation might be that 
  the project you’re working on has been put on hold. The cost of running a 
  cluster is split into two parts: Compute and Storage. The benefit here is 
  that while the cluster is suspended, you are only charged for the storage.

* **Delete cluster**
  All cluster data will be lost on deletion. This action cannot be undone.


.. _overview-community:

Community
=========

The Community link goes to the `CrateDB and CrateDB Cloud Community page`_.
Here you can ask members of the community and Crate.io employees questions
about uncertainties or problems you are having when using our products.

.. _aks1.eastus2.azure.cratedb.cloud: https://eastus2.azure.cratedb.cloud/
.. _eks1.eu-west-1.aws.cratedb.cloud: https://eks1.eu-west-1.aws.cratedb.cloud
.. _aks1.westeurope.azure.cratedb.cloud: https://aks1.westeurope.azure.cratedb.cloud/
.. _an organization admin: https://crate.io/docs/cloud/reference/en/latest/user-roles.html#organization-roles
.. _bregenz.a1.cratedb.cloud: https://bregenz.a1.cratedb.cloud/
.. _CIDR block: https://www.keycdn.com/support/what-is-cidr
.. _concepts: https://crate.io/docs/cloud/reference/en/latest/concepts.html
.. _CrateDB Admin UI: https://crate.io/docs/clients/admin-ui/
.. _CrateDB and CrateDB Cloud Community page: https://community.crate.io/
.. _CrateDB architecture documentation: https://crate.io/docs/crate/howtos/en/latest/architecture/shared-nothing.html
.. _CrateDB Cloud: https://crate.io/products/cratedb-cloud/
.. _CrateDB Cloud Console: https://console.cratedb.cloud
.. _CrateDB Cloud support: support@crate.io
.. _CrateDB Edge: https://crate.io/products/cratedb-edge/
.. _CrateDB Edge region: https://crate.io/docs/cloud/tutorials/en/latest/edge/index.html
.. _Croud: https://crate.io/docs/cloud/cli/en/latest/
.. _Croud clusters upgrade: https://crate.io/docs/cloud/cli/en/latest/commands/clusters.html#clusters-upgrade
.. _deploy a trial cluster on the CrateDB Cloud Console for free: https://crate.io/lp-free-trial
.. _glob: https://en.wikipedia.org/wiki/Glob_(programming)
.. _HTTP: https://crate.io/docs/crate/reference/en/latest/interfaces/http.html
.. _Microsoft Azure: https://azure.microsoft.com/en-us/
.. _PostgreSQL wire protocol: https://crate.io/docs/crate/reference/en/latest/interfaces/postgres.html
.. _scaling the cluster: https://crate.io/docs/cloud/howtos/en/latest/scale-cluster.html
.. _signup tutorial: https://crate.io/docs/cloud/tutorials/en/latest/sign-up.html
.. _tutorial: https://crate.io/docs/cloud/tutorials/en/latest/cluster-deployment/index.html
.. _user roles: https://crate.io/docs/cloud/reference/en/latest/user-roles.html
.. _wildcard: https://en.wikipedia.org/wiki/Wildcard_character
