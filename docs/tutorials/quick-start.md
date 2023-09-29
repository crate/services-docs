(quick-start)=

# Quick Start

The quickest and easiest way to get started with CrateDB is to create a new 
cluster in CrateDB Cloud. You can get started by following these simple steps:

## Create User

To create your user account you can either set up username and password or use 
one of the supported authentication providers:

````{tab} Username & Password
<br>

1. Register for an account on the [CrateDB Cloud sign-in page](https://console.cratedb.cloud/).
2. Click on **"Username & Password"** on the right side.
3. At the bottom press **"Sign up"** and create a new user.
4. Verify your email address by clicking the link in the confirmation email.
5. Log in using the username and password you just set up.
````

````{tab} Authentication Provider
<br>

1. Register for an account on the [CrateDB Cloud sign-in page](https://console.cratedb.cloud/).
2. Sign in using one of the authentication providers:
    - Microsoft
    - Google
    - GitHub
````

Once you signed in, you will be redirected to the CrateDB Cloud Console.

```{note}
- If you sign in through an external authentication provider, a CrateDB Cloud
  user account will be auto-generated for you.

- If your sign-up was not initiated through an invitation to a pre-existing
  CrateDB Cloud organization, a default organization named "My Organization"
  will be created automatically on your behalf. You can rename this organization
  later via the "Settings".
```

## Deploy Cluster

As next step we want to deploy our first CrateDB cluster. If you are still on the
**"Clusters"** page you can follow these steps:

1. Click on **"Deploy cluster"** in the middle of the screen.
2. Provide a cluster name, which will be part of the hostname of your cluster.
3. Select one of the available cloud regions.
4. Select the **"FREE"** compute size.
5. Click the blue **"Deploy Cluster"** button on the right side.

Once you deployed the cluster you will be redirected to the next screen.
CrateDB Cloud automatically generates a password for the `admin` user. You can 
change the password later if needed.

1. Copy the provided username and password.
2. Click **"OK"** on the bottom right.

You will be redirected to the cluster overview page. The cluster deployment 
might take a few minutes. Wait until the deployment is finished and you can read
"Healthy as of a few seconds ago" on the top left before continuing with the 
next step.

```{note}
- The **"FREE"** cluster can be started without providing payment details once 
  per organization.
- It will be suspended if not used for 7 consecutive days and will be deleted 
  after an additional 7 days of inactivity.
```

## Connect

Every CrateDB cluster comes with a built-in user interface. You can access it 
by clicking the blue **"Open Admin UI"** button. Alternatively you can also use
3rd party tools using the connecting details on the bottom of the page in the
**"Connecting to your cluster"** section.

1. Click on **"Open Admin UI"**.
2. In the newly opened page click on **"</>"** to open the query console.
3. Run your first query:
  ```sql
  SELECT *
  FROM sys.summits 
  LIMIT 20;
  ```

While the integrated `sys.summits` table can be used run your first queries, you
probably want to import your own data or start with one of our sample datasets.

## Import Data

To import data in a CrateDB Cloud cluster you can make use of the provided
import mechanism in the cloud console, which can be found next to the cluster 
overview page in the **"Import"** tab.

````{tab} Own Data
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

```sql
SELECT *
FROM my_table
LIMIT 100;
```
````

````{tab} Sample Dataset
<br>

1. Click on **"Import"** tab on the top menu.
1. Click on **"URL"** on the top right switch.
3. Click on **"Use our demo data set"** on the bottom left.
6. Click on the blue **"Import"** button.
7. Wait until the file is imported successfully

Using your preferred method (e.g. Admin UI) run the following query to display 
the first 100 records of the imported NYC taxi sample dataset:

```sql
SELECT *
FROM nyc_taxi
LIMIT 100;
```
````
