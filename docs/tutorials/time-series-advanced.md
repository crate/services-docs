(time-series-advanced)=

# Analyzing Device Readings with Metadata Integration

CrateDB is highly regarded as an optimal database solution for managing time-series data thanks to its unique blend of features. It is particularly effective when you need to combine time-series data with metadata, for instance, in scenarios where data like sensor readings or log entries, need to be augmented with additional context for more insightful analysis. CrateDB supports effective time-series analysis with fast aggregations, a rich set of built-in functions, and `JOIN` operations.

In this tutorial, we will illustrate how to augment time-series data with the metadata to enable more comprehensive analysis. To get started let’s use a time-series dataset that captures various device readings, such as battery, CPU, and memory information. Each record includes:

- `ts` - timestamp when each reading was taken.
- `device_id` - identifier of the device.
- `battery` - object containing battery level, status, and temperature.
- `cpu` -  object containing average CPU loads over the last 1, 5, and 15 minutes.
- `memory` - object containing information about the device's free and used memory.

The second dataset in this tutorial contains metadata information about various devices. Each record includes:

- `device_id` - identifier of the device.
- `api_version` - version of the API that the device supports.
- `manufacturer` - name of the manufacturer of the device.
- `model` - model name of the device.
- `os_name` - the name of the operating system running on the device.

## Creating the Table

CrateDB uses SQL, a powerful and familiar language for database management. To store the device readings and the device info data, create two tables with columns tailored to the datasets using the `CREATE TABLE` command:

```sql
CREATE TABLE IF NOT EXISTS doc.devices_readings (
   "ts" TIMESTAMP WITH TIME ZONE,
   "device_id" TEXT,
   "battery" OBJECT(DYNAMIC) AS (
      "level" BIGINT,
      "status" TEXT,
      "temperature" DOUBLE PRECISION
   ),
   "cpu" OBJECT(DYNAMIC) AS (
      "avg_1min" DOUBLE PRECISION,
      "avg_5min" DOUBLE PRECISION,
      "avg_15min" DOUBLE PRECISION
   ),
   "memory" OBJECT(DYNAMIC) AS (
      "free" BIGINT,
      "used" BIGINT
   )
);
```

```sql
CREATE TABLE IF NOT EXISTS doc.devices_info (
   "device_id" TEXT,
   "api_version" TEXT,
   "manufacturer" TEXT,
   "model" TEXT,
   "os_name" TEXT
);
```
Using objects in the `devices_readings` dataset allows for the structured and efficient organization of complex, nested data, enhancing both data integrity and flexibility. 

## Inserting Data

Now, insert the data using the `COPY FROM` SQL statement.

```sql
COPY doc.devices_info
FROM 'https://github.com/crate/cratedb-datasets/raw/main/cloud-tutorials/devices_info.json.gz'
WITH (compression='gzip', empty_string_as_null=true)
RETURN SUMMARY;
```
```sql
COPY doc.devices_readings
FROM 'https://github.com/crate/cratedb-datasets/raw/main/cloud-tutorials/devices_readings.json.gz'
WITH (compression='gzip', empty_string_as_null=true)
RETURN SUMMARY;
```
## Time-series Analysis with Metadata

To illustrate `JOIN` operation, the first query retrieves the 100 rows of combined data from two tables, `devices.readings` and `devices.info`, based on a matching `device_id` in both. It effectively merges the detailed readings and corresponding device information, providing a comprehensive view of each device's status and metrics.

```sql
SELECT *
FROM devices.readings r
JOIN devices.info i ON r.device_id = i.device_id
LIMIT 100;
```

The next query illustrates the calculation of summaries for aggregate values. In particular, it finds average battery levels (`avg_battery_level`) for each day and shows the result in an ascending order.

```sql
SELECT date_trunc('day', ts) AS "day", AVG(battery['level']) AS avg_battery_level
FROM doc.devices_readings
GROUP BY "day"
ORDER BY "day";
```
Rolling averages are crucial in time-series analysis because they help smooth out short-term fluctuations and reveal underlying trends by averaging data points over a specified period. This approach is particularly effective in mitigating the impact of outliers and noise in the data, allowing for a clearer understanding of the true patterns in the time series. 

The following example illustrates the average (`AVG`), minimum (`MIN`), and maximum (`MAX`) battery temperature over a window of the last 100 temperature readings (`ROWS BETWEEN 100 PRECEDING AND CURRENT ROW`). The window is defined in descending order by timestamp (`ts`) and can be adapted to support different use cases. 

```sql
SELECT r.device_id,
       AVG(battery['temperature']) OVER w AS "last 100 temperatures",
       MIN(battery['temperature']) OVER w AS "min temperature",
       MAX(battery['temperature']) OVER w AS "max temperature"
FROM doc.devices_readings r
JOIN doc.devices_info i ON r.device_id = i.device_id
WHERE battery['temperature'] > 100
    AND model = 'mustang'
WINDOW w AS (ORDER BY "ts" DESC ROWS BETWEEN 100 PRECEDING AND CURRENT ROW);
```
The next query shows how to extract the most recent reading for each device of the _mustang_ model. The query selects the latest timestamp (`MAX(r.ts)`), which represents the most recent reading time, and the corresponding latest readings for battery, CPU, and memory (`MAX_BY` for each respective component, using the timestamp as the determining factor). These results are grouped by `device_id`, `manufacturer`, and `model` to ensure that the latest readings for each unique device are included. This query is particularly useful for monitoring the most current status of specific devices in a fleet.

```sql
SELECT 
    MAX(r.ts) as time,
    r.device_id,
    MAX_BY(r.battery, r.ts) as battery,
    MAX_BY(r.cpu, r.ts) as cpu,
    MAX_BY(r.memory, r.ts) as memory,
    i.manufacturer,
    i.model
FROM 
    devices_readings r
JOIN 
    devices_info i ON r.device_id = i.device_id
WHERE 
    i.model = 'mustang'
GROUP BY 
    r.device_id, i.manufacturer, i.model;
```
Finally, we demonstrate the complex query that illustrates the usage of Common Table Expressions (CTEs) to aggregate and analyze device readings and information. The query relies on three CTEs to temporarily capture data:

- **MaxTimestamp CTE**: This CTE finds the most recent timestamp (`MAX(ts)`) in the `doc.devices_readings` table. It's used to focus the analysis on recent data.
- **DeviceReadingsAgg CTE**: This CTE calculates the average battery level and temperature for each device, but only for readings taken within the last week (as defined by `r.ts >= m.max_ts - INTERVAL '1 week'`). 
- **DeviceModelInfo CTE**: This CTE selects details from the `doc.devices_info` table, specifically the `device_id`, `manufacturer`, `model`, and `api_version`, but only for devices with an API version between 21 and 25.

The main `SELECT` statement joins the `DeviceReadingsAgg` and `DeviceModelInfo` CTEs, and aggregates data to provide the average battery level and temperature for each combination of manufacturer, model, and API version. It also proivdes the number of readings (`COUNT(*)`) for each grouping.

Overall, the query aims to provide a detailed analysis of the battery performance (both level and temperature) for devices with specific API versions, while focusing only on recent data. It allows for a better understanding of how different models and manufacturers are performing in terms of battery efficiency within a specified API range and time frame.

```sql
WITH 
max_timestamp AS (
    SELECT MAX(ts) AS max_ts
    FROM doc.devices_readings
),
DeviceReadingsAgg AS (
    SELECT 
        r.device_id,
        AVG(r.battery['level']) AS avg_battery_level,
        AVG(r.battery['temperature']) AS avg_battery_temperature
    FROM 
        doc.devices_readings r, MaxTimestamp m
    WHERE 
        r.ts >= m.max_ts - INTERVAL '1 week'
    GROUP BY 
        r.device_id
),
DeviceModelInfo AS (
    SELECT 
        device_id,
        manufacturer,
        model,
        api_version
    FROM 
        doc.devices_info
    WHERE 
        api_version BETWEEN 21 AND 25
)
SELECT 
    info.manufacturer,
    info.model,
    info.api_version,
    AVG(read.avg_battery_level) AS model_avg_battery_level,
    AVG(read.avg_battery_temperature) AS model_avg_battery_temperature,
    COUNT(*) AS readings_count
FROM 
    DeviceReadingsAgg read
JOIN 
    device_model_info info 
ON 
    read.device_id = info.device_id
GROUP BY 
    info.manufacturer, 
    info.model, 
    info.api_version
ORDER BY 
    model_avg_battery_level DESC;
```

In conclusion, this tutorial has guided you through the process of querying and analyzing time-series data with CrateDB, demonstrating how to effectively merge device metrics with relevant metadata. These techniques and queries are important for unlocking deeper insights into device performance, equipping you with the skills needed to harness the full potential of time-series data in real-world applications.