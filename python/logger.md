```python
import logging

logging.basicConfig(format='%(asctime)s - %(message)s', datefmt='%d-%b-%y %H:%M:%S', level='DEBUG')

logger = logging.getLogger('example_logger')
```
Levels:  
CRITICAL 50  
ERROR 40  
WARNING 30  
INFO 20  
DEBUG 10  
NOTSET 0  