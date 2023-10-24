(time-series)=

# Time-Series: Analyzing Weather Data

CrateDB is a powerful database designed to handle various use cases, one of
which is managing time series data. Time series data refers to collections of
data points recorded at specific intervals over time, like the hourly
temperature of a city or the daily sales of a store.

For this tutorial, imagine a dataset that captures weather
readings from CrateDB offices across the globe. Each record includes:

- `timestamp`: The exact time of the recording.
- `location`: The location of the weather station.
- `temperature`: The temperature in degrees Celsius.
- `humidity`: The humidity in percentage.
- `wind_speed`: The wind speed in km/h.

## Creating the Table

CrateDB uses SQL, a powerful and familiar language for database management. To
store the weather data, create a table with columns tailored to the
dataset using the `CREATE TABLE` command:

```sql
CREATE TABLE "weather_data" (
    "timestamp" TIMESTAMP,
    "location" VARCHAR,
    "temperature" DOUBLE,
    "humidity" DOUBLE,
    "wind_speed" DOUBLE
);
```

Run the above SQL command in CrateDB to set up your table. With the table ready,
you are now set to insert the dataset.


## Inserting Data

Insert the data using the `COPY FROM` SQL statement.
```sql
COPY weather_data
FROM 'https://github.com/crate/cratedb-datasets/raw/main/cloud-tutorials/data_weather.csv.gz'
WITH (format='csv', compression='gzip', empty_string_as_null=true);
```


## Analyzing Data

Start with a basic `SELECT` statement on all columns, and limit the output to
display only 10 records, in order to quickly explore a few samples worth of data.
```sql
SELECT *
FROM weather_data
LIMIT 10;
```

CrateDB is built for fast aggregation using the columnar storage to speed up
queries. For example, calculate the average temperature for each location by using the
`AVG` aggregation function:

```sql
SELECT location, AVG(temperature) AS avg_temp
FROM weather_data
GROUP BY location;
```

Computing basic averages is nothing special, but what if you need to answer more detailed
questions? For example, if you want to know the highest temperature for each
place and when it occurred.

Simple groupings might not be enough, but
thankfully, CrateDB has enhanced tools for time series data. You can use the
`max_by(returned_value, maximized_value)` function, which gives you a value (like
the time) when another value (like the temperature) is at its highest.

Let's put this to use with the following query:
```sql
SELECT location,
       max(temperature) AS highest_temp,
       max_by(timestamp, temperature) AS time_of_highest_temp
FROM weather_data
GROUP BY location;
```

You have probably observed by now, that there are gaps in the dataset for certain
metrics. Such occurrences are common, perhaps due to a sensor malfunction or
disconnection. To address this, the missing values need to be filled in. You can
employ another useful tool: window functions paired with the `IGNORE NULLS`
feature. Within a Common Table Expression (CTE), we utilize window functions to
spot the next and prior non-null temperature recordings, and then compute the 
arithmetic mean to bridge the gap:

```sql
WITH OrderedData AS (
    SELECT timestamp,
           location,
           temperature,
           LAG(temperature, 1) IGNORE NULLS OVER (ORDER BY timestamp) AS prev_temp,
           LEAD(temperature, 1) IGNORE NULLS OVER (ORDER BY timestamp) AS next_temp
    FROM weather_data
)
SELECT timestamp,
       location,
       temperature,
       (prev_temp + next_temp) / 2 AS interpolated_temperature
FROM OrderedData
ORDER BY location, timestamp
LIMIT 50;
```

This query retrieves the missing temperature values and interpolates them by
averaging the previous and next available temperature readings.
