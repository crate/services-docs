(time-series)=

# Time-Series: Analyzing Weather Data

CrateDB is a powerful database designed to handle various use cases, one of
which is managing time series data. Time series data refers to collections of
data points recorded at specific intervals over time, like the hourly
temperature of a city or the daily sales of a store.

In this tutorial, we'll dive into an imaginary dataset that captures weather
readings from CrateDB offices across the globe. Each data entry in our set will
include:

- `ts`: The exact time of the recording.
- `location`: The location of the weather station.
- `temperature`: The temperature in Celsius.
- `humidity`: The humidity in percentage.
- `wind_speed`: The wind speed in km/h.

## Creating the Table

CrateDB uses SQL, a powerful and familiar language for database management. To
store our weather data, we'll create a table with columns tailored to our
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
you're now set to insert the dataset.


## Inserting Data
With the table created we can now insert the data using the `COPY FROM` command
by using the table we just created and the source for our weather data:

```sql
COPY weather_data
FROM 'https://github.com/crate/cratedb-datasets/raw/main/cloud-tutorials/data_weather.csv.gz'
WITH (format='csv', compression='gzip', empty_string_as_null=true);
```

Run the above SQL command in CrateDB to import the dataset. After this commands 
finishes, we are now ready to analyse the weather data.

## Analyzing Data

Let us start with a simple `SELECT` on all columns and limiting the output to 10
results by running the following:

```sql
SELECT *
FROM weather_data
LIMIT 10;
```

CrateDB is build for fast aggregation using the columnar storage to speed up
queries. Let us calculate the average temperature for each location by using the
`AVG` aggregation function:

```sql
SELECT location, AVG(temperature) AS avg_temp
FROM weather_data
GROUP BY location;
```

Computing basic averages is easy, but what if we need to answer more detailed
questions? For example, if we want to know the highest temperature for each
place and when it occurred. Simple groupings might not be enough, but
thankfully, CrateDB has enhanced tools for time series data. We can use the
`max_by(returned_value, maximized_value)` function, which gives us a value (like
the time) when another value (like the temperature) is at its highest. Let's put
this to use with the following query:

```sql
SELECT location,
       max(temperature) AS highest_temp,
       max_by(timestamp, temperature) AS time_of_highest_temp
FROM weather_data
GROUP BY location;
```

We can see that the query returns the intended result.

You've probably observed by now that there are gaps in our dataset for certain
metrics. Such occurrences are common, perhaps due to a sensor malfunction or
disconnection. To address this, we need to fill in the missing values. We can
employ another useful tool: window functions paired with the `IGNORE NULLS`
feature. Within a CTE, we utilize window functions to spot the next and prior
non-null temperature recordings, and then compute the mean to bridge the gap:

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
