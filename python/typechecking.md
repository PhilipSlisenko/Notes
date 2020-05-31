
## Overriding types of function parameters
Problem:
```python
def func(a: Optional[list]) -> Optional[list]:
    return a
res = func([1, 2])
len(res) # Error cannot use len on None. Typechecker assumes None might be outputed by func
```
Solution: you can overload type definition for function:
```python
@overload
def func(a: list) -> list:
    pass

@overload
def func(a: None) -> None:
    pass

# Actual implementation
def func(a: Optional[list]) -> Optional[list]:
    return a
```
## Generics
Generics preserve some type throughout funtion (any namespace I suppose):
```python
from typing import Sequence, TypeVar

T = TypeVar('T')      # Declare type variable

def first(l: Sequence[T]) -> T:   # Generic function
    return l[0]
```
```python
from typing import TypeVar

AnyStr = TypeVar('AnyStr', str, bytes)

def concat(a: AnyStr, b: AnyStr) -> AnyStr:   
    return a + b

concat(b'a', 'b') # error
concat(b'a', b'b')
concat('a', 'b')
```
AnyStr is actualy part of typing module

## Ducktyping (checking adherence to protocol)
```python
from typing_extensions import Protocol

class Renderable(Protocol):
    def __render__(self) -> str: ...

def render(obj: Renderable):
    return obj.__render__()

class Foo(Renderable):
    def __render__(self):
        return 'rendered'

render(Foo())
render('a') # error expected Renderable
```
This feature is also called Structural subtyping (Foo is subtype of Bar because it follows specific structure). By contrast with Nominal subtyping (Foo is subtype of Bar just because)
___
If function returns Any according to type hints. But you need to specify what type it should be in this particular place in code, you can use `typing.cast`.
def func(a: str) -> int: ...
___
Instagrams monkeytype. Infer type at runtime, output stub file, add type hints to module.  
https://github.com/Instagram/MonkeyType  
Fast type checker from facebook  
https://github.com/facebook/pyre-check