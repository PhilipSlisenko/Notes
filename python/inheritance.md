super()  
When using super() self is passed to method automatically.  
`super().__init__('Dog')` instead of `Base.__init__(self, 'Dog')`. Benefit: we can easily change name of base class.  
The `super()` builtin returns a proxy object, a substitute object that can call methods of the base class via delegation. This is called indirection (ability to reference base object with `super()`)  
Since the indirection is computed at the runtime, we can use different base classes at different times (if we need to).  
`super()` can also take two parameters: the first is current class (subclass), and the second parameter is what will be passed to method as self or cls if classmethod. So:
```python
class Foo(Bar):
    def __init__(self):
        super().__init__() == super(Foo, self).__init__() == super(type(self), self).__init__() 
```