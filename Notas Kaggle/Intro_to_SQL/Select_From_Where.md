# Select From Where

```python
query = """
        SELECT city
        FROM `bigquery-public-data.openaq.global_air_quality`
        WHERE country = 'US'
        """
```

```python
# Create a "Client" object
client = bigquery.Client()
```

```python
# Set up the query
query_job = client.query(query)
```

```python
# API request - run the query, and return a pandas DataFrame
us_cities = query_job.to_dataframe()
```