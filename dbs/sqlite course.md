connect to **db** -> create a cursor

db(table(record))


## Connect to db
```python
conn = sqlite3.connect('customer.db') # will create if doesn't exist
```
Also you can create in memory db (lives in RAM, exists while process exists):
```python
conn = sqlite3.connect(':memory:')
```
## Create a cursor  
Tells database what you want to do  
```python 
c = conn.cursor()
```
## Create a table
When we want to do something in a database we execute SQL.  
Each field has type.  
```python 
c.execute("""
    CREATE TABLE customers (
        first_name text,
        last_name text,
        email text
    );
""")
```
## Commit (actually execute)
```python 
conn.commit()
```  
## Close connection
```python 
conn.close()
``` 