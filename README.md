from cloudera_loader import ClouderaVWLoader

# Cloudera Virtual Warehouse Loader
## An helper class to load CDW's tables into Langchain's Documents


### How to use it
Add the file to your PYTHON_PATH then run

```python
from cloudera_loader import ClouderaVWLoader

endpoint = "<Impala CDW Endpoint>"
database = "<CDW database to use>"
user = "<Cloudera Workload Username>"
password = "<Cloudera Workload password>"
```

Set up the query:

```python
query = "Select <field1>, <field2>, <field3> from <table>"
```

Define page_content columns and metadata columns:
```python
page_content_columns = ["<field1>"]
metadata_columns = ["field2", "<field3>"]
```

Run it
```python
cloudera_loader = ClouderaVWLoader(
    endpoint=endpoint,
    database=database,
    workload_user=user,
    workload_password=password,
    query=query,
    page_content_columns=page_content_columns,
    metadata_columns=metadata_columns,
)

cloudera_documents = cloudera_loader.lazy_load()

for doc in cloudera_documents:
    print(doc)
```

### Limitation
Currently, the loader has the following limitations:
* Only Impala Virtual Warehouses are supported
* Only LDAP authentication (with workload username and password) is supported





