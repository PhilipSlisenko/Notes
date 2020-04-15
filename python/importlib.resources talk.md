`import package as pkg`  
`pkg.__file__` points to `__init__.py` file of the package

importlib.resources are needed if you want to import some static data from package. Some file from inside package. But that package can be in .zip or some other obstacles.

``` python
from importlib.resources import read_binary
contents = read_binary('pkg.data', 'sample.dat') #it will read sample.dat data
```
Terminology of this talk:  
`package` - any importable module with a `__path__` attribute. In python package differs from module only that it has `__path__` attribute in it's object. (has `__init__.py` file)  
`resource` - any readable object contained in a package (`.py` file in package directory). Subdirectories and subpackages are not resources.

```python
read_binary(package: Package, resource: Resource) -> bytes
```

`importlib.resources.open_resource(recource: str)` 
`importlib.resources.contents`: like listdir for package 
`importlib.resources.is_resource(package, name)`: e.g. iterate using contents and check if is resource

During import. Finder looks for module, loader loads it.

sys.path, temporary files, **import system**, `__path__` attribute, namespace packages, resources, **namespaces**