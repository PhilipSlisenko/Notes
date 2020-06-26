```python
from setuptools import setup, find_packages

setup(
    name='sampleproject',
    version='1.3.1',
    packages=['pack'],
    py_modules=['foo'],
    entry_points={
        'console_scripts': [
            'sample=sample:main',
        ],
    },
)
```