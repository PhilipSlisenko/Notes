read csv from bytesIO
```python
from io import BytesIO
from csv import reader
csv_data = "some_string\nfor_example"
with BytesIO(csv_data) as input_file:
    csv_reader = reader(input_file, delimiter=",", quotechar='"')
    for row in csv_reader:
        print row
```
Read CSV
```python
with open(r'file', 'r') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=';')
    line_count = 0
    parsed_rows = list()
    # skip header
    next(csv_reader)
    for row in csv_reader:
        line_count += 1
        if line_count == 10:
            pass
```
Write CSV
```python
with open(scv_file, mode='w', newline='') as scv_file:
    writer = csv.writer(scv_file, delimiter=';', quotechar='"', quoting=csv.QUOTE_MINIMAL)
    writer.writerow(['Image Key', '"Label"'])
    for key, val in form_dict.items():
        writer.writerow([key, val])
```