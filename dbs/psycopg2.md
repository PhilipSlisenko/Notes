```python
conn = conn()
cur = cur()
try:
    dostuff()
finally:
    cur.close()
    conn.close()
```
becomes:
```python
with conn() as conn:
    with cur() as cur:
        dostuff()
```
___
```python
with conn() as conn:
    with cur() as cur:
        cur.execute('SELECT 1;')
        cur.fetchone()
```
___
```python
with conn() as conn:
    with cur() as cur:
        cur.execute()
        conn.commit()
        cur.execute()
        conn.commit()
``` 
### Savepoints
```python
with conn() as conn:
    with cur() as cur:
        cur.execute()
        cur.execute('CREATE TABLE ...')
        cur.execute('SAVEPOINT sp1;')
        try:
            cur.execute('INSERT INTO...')
        except:
            cur.execute('ROLLBACK TO SAVEPOINT sp1;')
        conn.commit()
```
___
### Returning (return rows with changes)
```python
query = "INSERT INTO users(name) VALUES ('John') RETURNING users.*"
# query = "DELETE FROM users RETURNING users.*"
with conn() as conn:
    with cur() as cur:
        cur.execute(query)
        row = cur.fetchone()
        conn.commit()
```
