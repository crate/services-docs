(quick-start)=

# Quick Start

The quickest and easiest way to get started with CrateDB is to create a new 
cluster in CrateDB Cloud. You can get started by following these simple steps:

## Create User

To create your user account, you can either set up username and password, or use
one of the supported authentication providers:

:::{tab} Username & Password
<br>

1. Register for an account on the [CrateDB Cloud sign-in page](https://console.cratedb.cloud/).
2. Click on **"Username & Password"** on the right side.
3. At the bottom press **"Sign up"** and create a new user.
4. Verify your email address by navigating to the link in the confirmation email.
5. Log in using the username and password you just set up.
:::

:::{tab} Authentication Provider
<br>

1. Register for an account on the [CrateDB Cloud sign-in page](https://console.cratedb.cloud/).
2. Sign in using one of the authentication providers:
    - Microsoft
    - Google
    - GitHub
:::

Once you signed in, you will be redirected to the CrateDB Cloud Console.

:::{note}
- If you sign in through an external authentication provider, a CrateDB Cloud
  user account will be auto-generated for you.

- If your sign-up was not initiated through an invitation to a pre-existing
  CrateDB Cloud organization, a default organization named "My Organization"
  will be created automatically on your behalf. You can rename this organization
  later via the "Settings".
:::

(deploy-cluster)=
## Deploy Cluster

As next step, let's deploy the first CrateDB cluster. If you are still viewing the
**"Clusters"** page, please follow these steps:

1. Click on **"Deploy cluster"** in the middle of the screen.
2. Provide a cluster name, which will be part of the hostname of your cluster.
3. Select one of the available cloud regions.
4. Select the **"FREE"** compute size.
5. Click the blue **"Deploy Cluster"** button on the right side.

Once you deployed the cluster, you will be redirected to the next screen.
CrateDB Cloud automatically generates a password for the `admin` user. You can 
change the password later if needed.

1. Copy the provided username and password.
2. Click **"OK"** on the bottom right.

You will be redirected to the cluster overview page. The cluster deployment 
might take a few minutes. Hold on until the deployment is finished, which will be indicated by
a corresponding "Healthy as of a few seconds ago" message on the top left, before continuing
with the next step.

:::{note}
- The **"FREE"** cluster can be started without providing payment details.
  You can use one free cluster per organization.
- The cluster will be suspended if not used for 4 consecutive days, and will be deleted
  after an additional 10 days of inactivity.
:::

## Connect

Each CrateDB cluster comes with a built-in user interface. You can access it
by selecting the blue **"Open Admin UI"** button. Alternatively, explore the
3rd party tools using the connecting details on the bottom of the page in the
**"Connecting to your cluster"** section.

1. Click on **"Open Admin UI"**, and provide authentication credentials.
2. In the newly opened page click on **"</>"** to open the query console.
3. Run your first query:
  :::{code} sql
  SELECT *
  FROM sys.summits 
  LIMIT 20;
  :::

While the integrated `sys.summits` table can be used to run your first queries, you
probably want to import your own data or start with one of our sample datasets.

## Import Data

To import data in a CrateDB Cloud cluster, you can make use of the provided
import mechanism in the cloud console, which can be found next to the cluster 
overview page in the **"Import"** tab.

::::{tab} Own Data
<br>

1. Click on **"Import"** tab on the top menu.
2. Drag and drop a file on the drop section or click **"browse"** to locate the
  file manually.
3. Select a file from your local disk.
4. Provide a valid table name e.g. `my_table`.
5. Adjust **"Format"** and **"Compression"** if necessary.
6. Click on the blue **"Import"** button.
7. Wait until the file is imported successfully

Using your preferred method (e.g. Admin UI) run the following query to display 
the first 100 records of your imported data.

:::{code} sql
SELECT *
FROM my_table
LIMIT 100;
:::
::::

::::{tab} Sample Dataset
<br>

1. Click on **"Import"** tab on the top menu.
1. Click on **"URL"** on the top right switch.
3. Click on **"Use our demo data set"** on the bottom left.
6. Click on the blue **"Import"** button.
7. Wait until the file is imported successfully

Using your preferred method (e.g. Admin UI) run the following query to display 
the first 100 records of the imported NYC taxi sample dataset:

:::{code} sql
SELECT *
FROM nyc_taxi
LIMIT 100;
:::
::::


## Usage

Learn how to use key features of CrateDB SQL using fundamental tutorials,
or explore {ref}`guide:features`.


:::::{grid} auto 2 2 2
:margin: 4 4 0 0
:padding: 0
:gutter: 2

::::{grid-item-card} {material-outlined}`data_object;2em` Document Store: The OBJECT Data Type
:link: guide:objects-basics
:link-type: ref
:class-footer: text-smaller

CrateDB’s `OBJECT` data type allows to store and analyze complex and nested data
efficiently. It can optionally be strict or dynamic, thus schemaless.

The tutorial explores analyzing marketing data, therefore it also outlines another
feature of CrateDB, supporting destructuring URLs by using generated columns.
+++
CrateDB's document store is based on Lucene indexes, exactly how Elasticsearch
is doing it.
::::

::::{grid-item-card} {material-outlined}`topic;2em` Time Series: Device Readings with Metadata
:link: guide:timeseries-objects
:link-type: ref
:class-footer: text-smaller

CrateDB supports effective time series analysis with enhanced features
for fast aggregations.

- Rich data types for storing structured nested data (OBJECT) alongside
  time series data.
- A rich set of built-in functions for aggregations.
- Relational JOIN operations.
- Common table expressions (CTEs).
+++
Combine time series data with document data: CrateDB is all you need.
::::

::::{grid-item-card} {material-outlined}`search;2em` Full-Text: Explore the Netflix Catalog
:link: guide:search-basics
:link-type: ref
:class-footer: text-smaller
CrateDB's `TEXT INDEX USING FULLTEXT` SQL DDL clause sets up a full-text index
on a column. The `MATCH` SQL predicate is used for querying it.

The tutorial explores the Netflix Catalog, exercising FTS features on relevant data.
+++
CrateDB's full-text search is based on Lucene's inverted index and BM25 scoring.
::::

::::{grid-item-card} {material-outlined}`lightbulb;2em` Time Series: Advanced SQL
:link: guide:timeseries-analysis-weather
:link-type: ref
:class-footer: text-smaller
CrateDB provides enhanced features for querying time series data.

Run aggregations with gap filling / interpolation, using common
table expressions (CTEs) and LAG / LEAD window functions.

Find maximum values using the MAX_BY aggregate function, returning
the value from one column based on the maximum or minimum value of another
column within a group.

The tutorial analyzes data from synoptic weather observations.
+++
Advanced queries on time series data: CrateDB is all you need.
::::


:::::
