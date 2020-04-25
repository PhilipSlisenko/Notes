Convert bytes to text on the go
```python
input = io.BytesIO(
        b'Inital value for read buffer with unicode characters ' +
        'ÁÇÊ'.encode('utf-8')
    )
wrapper = io.TextIOWrapper(input, encoding='utf-8')
```
```python
with open(r"", "r+b") as f:
    new = f.read().decode('ANSI').replace(',', ';').encode('ANSI')
    f.truncate(0)
    f.seek(0)
    f.write(new)
```