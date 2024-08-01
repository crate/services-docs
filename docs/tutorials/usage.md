(usage)=

# Using SQL on CrateDB Cloud

Learn how to use key features of CrateDB SQL using fundamental tutorials,
or explore {ref}`guide:features`.

<style>
/* Cards with Links */
.sd-hide-link-text {
  height: 0;
}
</style>


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
