# cython for C++

ref:

- http://cython.readthedocs.io/en/latest/src/userguide/wrapping_CPlusPlus.html

# compilation

```python
from distutils.core import setup
from Cython.Build import cythonize

setup(ext_modules = cythonize(
           "rect.pyx",                 # our Cython source
           sources=["Rectangle.cpp"],  # additional source file(s)
           language="c++",             # generate C++ code
      ))
```

# declaring the C++ class

```cython
cdef extern from "Rectangle.h" namespace "shapes":  # make class def for `Rectangle` available
    cdef cppclass Rectangle:  # define the class
    	# the method declarations
        Rectangle() except + 
        Rectangle(int, int, int, int) except +  # rasie the exception if needed
        int x0, y0, x1, y1
        int getArea()
        void getSize(int* width, int* height)
        void move(int, int)
```

# wrapping it in Cython

common practice: hold a C++ instance which we're wrapping as an attribute

```cython
cdef class PyRectangle:  # this is a Cython class, which will be converted to C++
    # hold a C++ instance which we're wrapping
    # assuming c_rect has a nullary constructor
    cdef Rectangle c_rect      

    def __cinit__(self, int x0, int y0, int x1, int y1):
        self.c_rect = Rectangle(x0, y0, x1, y1)
    def get_area(self):
        return self.c_rect.getArea()
    def get_size(self):
        cdef int width, height
        self.c_rect.getSize(&width, &height)
        return width, height
    def move(self, dx, dy):
        self.c_rect.move(dx, dy)

    # getter and setter
    @property
    def x0(self):
        return self.c_rect.x0

    @x0.setter
    def x0(self):
        def __set__(self, x0): self.c_rect.x0 = x0
```

without nullary constructor

```cython
cdef class PyRectangle:
    # hold a **pointer** to the C++ instance which we're wrapping
    cdef Rectangle* c_rect      

    # initialized upon creation of the Python instance
    def __cinit__(self, int x0, int y0, int x1, int y1):
        self.c_rect = new Rectangle(x0, y0, x1, y1)

    # deleted upon deletion of the Python instance
    def __dealloc__(self):
        del self.c_rect
```

with default constructor

no need for `__cint__` and `__dealloc__`. automatically created by Cython


# overloading

function

```cython
cdef extern from "Foo.h":
    cdef cppclass Foo:
        Foo(int)  # specified by the argument type
        Foo(bool)
        Foo(int, bool)
        Foo(int, int)
```

operator (similar)

```cython
cdef extern from "foo.h":
    cdef cppclass Foo:
        Foo()
        Foo operator+(Foo)
        Foo operator-(Foo)
        int operator*(Foo)
        int operator/(int)

cdef Foo foo = new Foo()  # is foo is pointer or value (using `new`)?

foo2 = foo + foo
foo2 = foo - foo

x = foo * foo2
x = foo / 1

```

## pointer and dereferencing

```cython
cdef Foo* foo_ptr = new Foo()  # foo_ptr is a pointer
foo = foo_ptr[0] + foo_ptr[0]  # foo_ptr[0] is equal to *foo_ptr in C
x = foo_ptr[0] / 2

del foo_ptr
```


# incompatible operators and alternative

- `++`: `cython.operator.preincrement` and `cython.operator.postincrement`
- dereference: `cython.operator.dereference`

to use it:

`from cython.operator cimport dereference as deref`

# templates

examples:

```cython
from cython.operator cimport dereference as deref, preincrement as inc

cdef extern from "<vector>" namespace "std":  # using vector from std
    cdef cppclass vector[T]:  # the template parameter
        cppclass iterator:
            T operator*()
            iterator operator++()
            bint operator==(iterator)
            bint operator!=(iterator)
        vector()
        void push_back(T&)
        T& operator[](int)
        T& at(int)
        iterator begin()
        iterator end(
```

another simpler:

```cython
cdef extern from "<algorithm>" namespace "std":
    T max[T](T a, T b)

print max[long](3, 4)
print max(1.5, 2.5)  # simple template argument deduction
```

the syntax:

`name[type]`

# C++ std

many std stuff are already declared in `pxd` files located in `/Cython/Includes/libcpp`. 

example of `vector`:

```cython
from libcpp.vector cimport vector  # import that this

cdef vector[int] vect
vect.push_back(...)
```



some automatic conversion is done also. 

```cython
from libcpp.string cimport string
from libcpp.vector cimport vector

cdef string s = py_bytes_object
print(s)
cpp_string = <string> py_unicode_object.encode('utf-8')

cdef vector[int] vect = xrange(1, 10, 2)  # iterable to vector
print(vect)              # [1, 3, 5, 7, 9]

cdef vector[string] cpp_strings = b'ab cd ef gh'.split()  # iterable to vector and bytes to string
print(cpp_strings[1])   # b'cd'
```

other examples, `std::set`, `std::pair`, `std::list`

# static method

in C++

```c++
static void do_something();
```

in Cython

```cython
@staticmethod
void do_something()
```

# using reference

standard `Type&` syntax

# `auto` keyword

```cython
cdef vector[int] v = ...
it = v.begin()  # deduced automatically. it's a long name
```

