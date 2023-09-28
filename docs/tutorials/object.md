(object)=

# Objects: Analyzing Marketing Data

As marketers, we often handle multi-structured data from different platforms.
CrateDB's dynamic `OBJECT` data type allows us to store and analyze this complex,
nested data efficiently. In this tutorial, we'll explore how to leverage this
feature in marketing data analysis, along with the use of generated columns to
parse and manage URLs.

Consider we have marketing data that captures details of various campaigns:

```json
{
    "campaign_id": "c123",
    "source": "Google Ads",
    "metrics": {
        "clicks": 500,
        "impressions": 10000,
        "conversion_rate": 0.05
    },
    "landing_page_url": "https://example.com/products?utm_source=google"
}
```

To begin, let's create the schema for this dataset:

## Creating the Table

CrateDB uses SQL, a powerful and familiar language for database management. To
store our marketing data, we'll create a table with columns tailored to our
dataset using the `CREATE TABLE` command:

```sql
CREATE TABLE marketing_data (
    campaign_id TEXT PRIMARY KEY,
    source TEXT,
    metrics OBJECT(DYNAMIC) AS (
        clicks INTEGER,
        impressions INTEGER,
        conversion_rate DOUBLE PRECISION
    ),
    landing_page_url TEXT,
    url_parts GENERATED ALWAYS AS parse_url(landing_page_url)
);
```

In this table definition:

- The `metrics` column is set up as an `OBJECT` featuring a dynamic structure.
  This enables you to perform flexible queries on its nested attributes like
  clicks, impressions, and conversion rate.
- Additionally, a generated column named `url_parts` is configured to
  automatically parse the `landing_page_url`. This makes it more convenient for
  you to query specific components of the URL later on.

The table is designed to accommodate both fixed and dynamic attributes,
providing a robust and flexible structure for storing your marketing data.


## Inserting Data
With the table created we can now insert the data using the COPY FROM command by
using the table we just created and the source for our marketing data:

```sql
COPY marketing_data
FROM 'https://github.com/crate/cratedb-datasets/raw/main/cloud-tutorials/data_marketing.json.gz'
WITH (format = 'json', compression='gzip');
```

## Analyzing Data

Let us start with a simple `SELECT` on the `metrics` column and limiting the
output to 10 results by running the following:

```sql
SELECT metrics
FROM marketing_data
LIMIT 10;
```

We can see that the `metrics` column returns an object in the form of a JSON.
If we just want to return a single property of this object we can adjust the
query slightly by adding the property to the selection using bracket notation.

```sql
SELECT metrics['clicks']
FROM marketing_data
LIMIT 10;
```

It's helpful to select individual properties from a nested object, but what if
we also want to filter results based on these properties? For instance, to find
`campaign_id` and `source` where `conversion_rate` exceeds `0.09`, we can employ
the same bracket notation for filtering as well.

```sql
SELECT campaign_id, source
FROM marketing_data
WHERE metrics['conversion_rate'] > 0.09
LIMIT 50;
```

This allows us to narrow down our query results while still leveraging CrateDB's
ability to query nested objects effectively.

Finally, let's explore data aggregation based on UTM source parameters. The
`url_parts` generated column, which is populated using the `parse_url()`
function, automatically splits the URL into its constituent parts upon data
insertion.

To analyze the UTM source, we can directly query these parsed parameters. The
goal is to count the occurrences of each UTM source and sort them in descending
order. This lets us easily gauge marketing effectiveness for different sources,
all while taking advantage of CrateDB's powerful generated columns feature.


```sql
SELECT
    url_parts['parameters']['utm_source'] AS utm_source,
    COUNT(*)
FROM marketing_data
GROUP BY 1
ORDER BY 2 DESC;
```

In this tutorial, we explored the versatility and power of CrateDB's dynamic
`OBJECT` data type for handling complex, nested marketing data.