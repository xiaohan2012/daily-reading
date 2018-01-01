# cython tutorial notes

refs:

- http://cython.readthedocs.io/en/latest/src/tutorial/cython_tutorial.html
- http://cython.readthedocs.io/en/latest/src/userguide/language_basics.html#language-basics

# compilation

```python
from distutils.core import setup
from Cython.Build import cythonize

setup(
    ext_modules = cythonize("helloworld.pyx")
)
```

and run

`$ python setup.py build_ext --inplace`

If your module doesn’t require any extra C libraries or a special build setup, then you can use the pyximport module

```python
import pyximport; pyximport.install()  # put this in front
```

# variable declaration

## `cdef`

declare C variables.

```cython
cdef int i, j, k

cdef struct Grail:
    int age
    float volume
```

grouping declarations together

```cython
cdef:
    struct Spam:
        int tons

    int i
    float a
    Spam *p
```


## `ctypedef`

`ctypedef unsigned long ULong` like `typedef` in C++


# python function vs C functions

> Python functions: using `def` statement. Take Python objects and return Python objects.
> C functions: using `cdef` statement. Take either Python objects or C values, and return either Python objects or C values.

they can call each other freely inside Cython while only Python functions can be called outside in the module. 


`cpdef` a hybrid approach: when called inside Cython, it uses C functions, otherwise as python function

## parameter type conversion

When a parameter of a Python function is declared to have a *C data type*, it is passed in as a *Python object* and automatically converted to a C value, if possible.


```cython
def spam(int i, char *s):
    pass
```

equivalent to

```cython
def spam(python_i, python_s):
    cdef int i = python_i
    cdef char* s = python_s
```

Automatic conversion is currently only possible for *numeric types, string types and structs*. 

## Python objects as parameters

```cython
cdef spamobjs(x, y):
    ...
```

takes in two Python objects

you can use `object` to declare something as a Python object

```cython
cdef ftang(object int):  # parameter type is Python object
    pass

cdef object ftang(object int):  # return type is Python object
    pass
```

## raise exception in `cdef`

designed for C functions returning integer, enum, float or pointer type

```cython
cdef int spam() except -1:
    ...
```

note that if the function returns normally, never return `-1`, because it will be treated as a exception.

variants:

- `except? -1`: all return values are possible, generates a call to `PyErr_Occurred()`
- `except *`: void function can only use this 
- `except +`: for C++


# string

a pointer `char *` to the contents of the Python string is used. 

it's better to copy the string as the actual Python string cannot live forever.


# syntax difference

- `p.x` not `p->x`
- `p[0]` not `*p`
- `<char*>q` for type conversion

# direct call to Python/C API functions

speed-up

examples:

- `abs`: `PyNumber_Absolute`
- `len`: `PyObject_Length`

# for loops

```python
for i in range(n):
    ...
```
If `i` is declared as a `cdef` integer type, it will optimise this into a *pure C loop*

these also work:

```cython
for i from 0 <= i < n:
    ....

for i from 0 <= i < n by s:
    ....
```


`n > i >= 0` also works.

# include files

```cython
include "spamstuff.pxi"
```

just like `#include` in C/C++

# conditional compilation

## Compile-Time Definitions

```cython
DEF FavouriteFood = u"spam"
DEF ArraySize = 42
DEF OtherArraySize = 2 * ArraySize + 17
```

## Conditional Statements
similar to `#if` preprocessor directive in C

```cython
IF UNAME_SYSNAME == "Windows":
    include "icky_definitions.pxi"
ELIF UNAME_SYSNAME == "Darwin":
    include "nice_definitions.pxi"
ELIF UNAME_SYSNAME == "Linux":
    include "penguin_definitions.pxi"
ELSE:
    include "other_definitions.pxi"
```


