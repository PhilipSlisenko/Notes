connect to **db** -> create a cursor

db(table(record))
___
# Inserting data
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
## Create a table, Insert
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
c.execute("""
    INSERT INTO customers VALUES ('name', 'surname', 'ns@mail.com');
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
`connection.execute()` is a nonstandard shortcut that creates an intermediate cursor object:
>`Connection.execute`  
This is a nonstandard shortcut that creates a cursor object by calling the cursor() method, calls the cursor’s execute() method with the parameters given, and returns the cursor. 

>Using the nonstandard `execute(), executemany() and executescript()` methods of the `Connection` object, your code can be written more concisely because you don’t have to create the (often superfluous) Cursor objects explicitly. Instead, the Cursor objects are created implicitly and these shortcut methods return the cursor objects. This way, you can execute a SELECT statement and iterate over it directly using only a single call on the Connection object.  
___
# Fetching data
## Connect to db
## Create a cursor 
## Query the database 
```python 
c.execute("""SELECT * FROM customers;""")
```
## Fetch
```python 
c.fetchone()
c.fetchmany(n)
c.fetchall()
```  
## Close connection
```python 
conn.close()
``` 
## Cursor  
You need a cursor object to fetch results. If you tried to do a SELECT without a cursor, you'd have no way to get the resulting data.  
Cursor objects allow you to keep track of which result set is which, since it's possible to run multiple queries before you're done fetching the results of the first.  
It gives us the ability to have multiple separate working environments through the same connection to the database.  

Cursor per operation.  
So maybe cursor is like a staging area
___
# Update, Delete, Drop
```python 
c.execute("""UPDATE ...""")
c.execute("""DELETE ...""")
c.execute("""DROP TABLE ...""")
conn.commit()
```
___
# D
```python 
c.execute("""UPDATE ...""")
c.execute("""DELETE ...""")
conn.commit()
```
## Workflow
create tables -> insert data -> query data