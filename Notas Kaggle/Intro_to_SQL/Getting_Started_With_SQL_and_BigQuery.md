# Getting Started With SQL and BigQuery

Para usar BigQuery
```python
from google.cloud importbigquery
```

Se crea un objecto **Client**
```python
client = bigquery.Client()
```

```python
#Se crea una referencia al dataset
dataset_ref = client.dataset("hacker_news", project = "bigquery-public-data")

#Api Request - fetch the dataset
dataset = client.get_dataset(dataset_ref)
```

```python
#Listar todas las tablas en "hacker_news"
tables = list(client.list_tables(dataset))

#Imprimir los nombres de las tablas
for table in tables:
    print(table.table_id)
```

Para obtener la referencia a una tabla
```python
table_ref = dataset_ref.table("full")

table = client.get_table(table_ref)
```

Para imprimir la información en la tabla "full"
```python
table.schema
```