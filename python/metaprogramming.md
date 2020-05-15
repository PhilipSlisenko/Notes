`vars(cls)` === `cls.__dict__`  
`setattr(cls, key, val)` set key val to `cls.__dict__`  
`getattr(object, 'x')` is completely equivalent to `object.x`. There's two cases where getattr can be useful:
- you can't write object.x, because you don't know in advance which attribute you want (it comes from a string). very useful for meta-programming.
- you want to provide a default value. object.y will raise an AttributeError if there's no y. But getattr(object, 'y', 5) will return 5.

`globals()` print globals namespace dict of the module. If called from function or method it prints 
globals of module where it is defined not where called.  
`locals()`  
`globals vs locals(bound) vs free variables` If a name is bound in a block, it is a local variable of 
that block, unless declared as nonlocal. If a name is bound at the module level, it is a global 
variable. (The variables of the module code block are local and global.) If a variable is used in a 
code block but neither global nor bound, it is a **free variable**. Free variables are needed for closures (not global not local but used). Python uses **lexical scope**, it is able to identify scope by parsing code.  
`callable()`  

`type` is a class that creates classes (aka types)
Class is a dictionary.

## How class is created? Class definition process
```python
class Spam(Base):
    def __init__(self):
        pass
    def bar(self):
        pass
```
**1 step** Body of class is isolated  
```python
body = """
    def __init__(self):
        pass
    def bar(self):
        pass
"""
```
**2 step** Class dictionary is created  
```python
clsdict = type.__prepare__('Spam', (Base,))
```
**3 step** Body is executed in returned dict  
```python
exec(body, globals(), clsdict)
```
Body string is executed in of `clsdict` and `clsdict` gets populated with all the methods from `body`.  
Now clsdict is:
```
{'__init____': <function __init__ at 0x7f5063b961e0>, 'bar': <function bar at 0x7f5063b961e0>}
```   
**4  step** class is constructed from its name, bases and clsdict  
```python
Spam = type('Spam', (Base,), clsdict) # <class '__main__.Spam'>
s = Spam()
s.bar()
```

`__new__` handles object creation and `__init__` handles object initialization



My takeaway:
Everything is a dict the question is which dict is passed where.  
Namespace is dict, object is dict, class is dict, scope is dict, module is dict, function is a dict. MRO surfes dicts. Scope == Namespace == Symbol table. Module, class, object, function have their own namespaces. Highest namespace is module namespace.