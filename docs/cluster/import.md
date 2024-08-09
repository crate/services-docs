(cluster-import)=
# Import 

The first thing you see in the "Import" tab is the history of your
imports. You can see whether you imported from a URL or from a file,
file name, table into which you imported, date, and status. By clicking
"Show details" you can display details of a particular import.

Clicking the "Import new data" button will bring up the Import page,
where you can select the source of your data.

If you don't have a dataset prepared, we also provide an example in the
URL import section. It's the New York City taxi trip dataset for July
of 2019 (about 6.3M records).

(cluster-import-url)=
## Import from URL 

To import data, fill out the URL, name of the table which will be
created and populated with your data, data format, and whether it is
compressed.

If a table with the chosen name doesn't exist, it will be automatically
created.

The following data formats are supported:

-   CSV (all variants)
-   JSON (JSON-Lines, JSON Arrays and JSON Documents)
-   Parquet

Gzip compressed files are also supported.

![Cloud Console cluster upload from URL](../_assets/img/cluster-import-tab-url.png)

(cluster-import-s3)=
## Import from private S3 bucket 

CrateDB Cloud allows convenient imports directly from S3-compatible
storage. To import a file form bucket, provide the name of your bucket,
and path to the file. The S3 Access Key ID, and S3 Secret Access Key are
also needed. You can also specify the endpoint for non-AWS S3 buckets.
Keep in mind that you may be charged for egress traffic, depending on
your provider. There is also a volume limit of 10 GiB per file for S3
imports. The usual file formats are supported - CSV (all variants), JSON
(JSON-Lines, JSON Arrays and JSON Documents), and Parquet.

![Cloud Console cluster upload from S3](../_assets/img/cluster-import-tab-s3.png)

:::{note}
It's important to make sure that you have the right permissions to
access objects in the specified bucket. For AWS S3, your user should
have a policy that allows GetObject access, for example:

 :::{code}
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
 :::
:::

(cluster-import-azure)=
## Import from Azure Blob Storage Container 

Importing data from private Azure Blob Storage containers is possible
using a stored secret, which includes a secret name and either an Azure
Storage Connection string or an Azure SAS Token URL. An admin user at
the organization level can add this secret.

You can specify a secret, a container, a table and a path in the form
[/folder/my_file.parquet]

As with other imports Parquet, CSV, and JSON files are supported. File
size limitation for imports is 10 GiB per file.

![Cloud Console cluster upload from Azure Storage Container](../_assets/img/cluster-import-tab-azure.png)

(cluster-import-globbing)=
## Importing multiple files 

Importing multiple files, also known as import globbing is supported in
any s3-compatible blob storage. The steps are the same as if importing
from S3, i.e. bucket name, path to the file and S3 ID/Secret.

Importing multiple files from Azure Container/Blob Storage is also
supported: `/folder/*.parquet`

Files to be imported are specified by using the well-known
[wildcard](https://en.wikipedia.org/wiki/Wildcard_character) notation,
also known as "globbing". In computer programming,
[glob](https://en.wikipedia.org/wiki/Glob_(programming)) patterns
specify sets of filenames with wildcard characters. The following
example would import all the files from the single specified day.

:::{code} console
/somepath/AWSLogs/123456678899/CloudTrail/us-east-1/2023/11/12/*.json.gz
:::

![Cloud Console cluster import globbing](../_assets/img/cluster-import-globbing.png)

As with other imports, the supported file types are CSV, JSON, and
Parquet.

(cluster-import-file)=
## Import from file 

Uploading directly from your computer offers more control over your
data. From the security point of view, you don't have to share the data
on the internet just to be able to import it to your cluster. You also
have more control over who has access to your data. Your files are
temporarily uploaded to a secure location managed by Crate (an S3 bucket
in AWS) which is not publicly accessible. The files are automatically
deleted after 3 days. You may re-import the same file into multiple
tables without having to re-upload it within those 3 days. Up to 5 files
may be uploaded at the same time, with the oldest ones being
automatically deleted if you upload more.

![Cloud Console cluster upload from file](../_assets/img/cluster-import-tab-file.png)

As with other import, the supported file formats are:

-   CSV (all variants)
-   JSON (JSON-Lines, JSON Arrays and JSON Documents)
-   Parquet

There is also a limit to file size, currently 1GB.

(overview-cluster-import-schema-evolution)=
## Schema evolution 

Schema Evolution, available for all import types, enables automatic
addition of new columns to existing tables during data import,
eliminating the need to pre-define table schemas. This feature is
applicable to both pre-existing tables and those created during the
import process. It can be toggled via the 'Schema Evolution' checkbox
on the import page.

Note that Schema Evolution is limited to adding new columns; it does not
modify existing ones. For instance, if an existing table has an
'OrderID' column of type **INTEGER**, and an import is
attempted with Schema Evolution enabled for data where 'OrderID'
column is of type **STRING**, the import job will fail due to
type mismatch.


## File Format Limitations 

**CSV** files:

1.  Comma, tab and pipe delimiters are supported.

**JSON** files:

The following formats are supported for JSON:

1.  JSON Documents. Will insert as a single row in the table.

    :::{code} console
    {
      "id":1,
      "text": "example"
    }
    :::

2.  JSON Arrays. Will insert as a row per array item.

    :::{code} console
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
    :::

3.  JSON-Lines. Each line will insert as a row.

    :::{code} console
    {"id":1, "text": "example"}
    {"id":2, "text": "example2"}
    :::
