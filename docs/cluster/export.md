(cluster-export)=
# Export 

The "Export" section allows users to download specific tables/views. When you
first visit the Export tab, you can specify the name of a table/view,
format (CSV, JSON, or Parquet) and whether you'd like your data to be
gzip compressed (recommended for CSV and JSON files).

:::{important}
-   Size limit for exporting is 1 GiB
-   Exports are held for 3 days, then automatically deleted
:::

:::{note}
**Limitations with Parquet**:
Parquet is a highly compressed data format for very efficient storage of
tabular data. Please note that for OBJECT and ARRAY columns in CrateDB,
the exported data will be JSON encoded when saving to Parquet
(effectively saving them as strings). This is due to the complexity of
encoding structs and lists in the Parquet format, where determining the
exact schema might not be possible. When re-importing such a Parquet
file, make sure you pre-create the table with the correct schema.
:::




