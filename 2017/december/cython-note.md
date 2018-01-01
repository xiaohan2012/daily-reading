# declared a struct from external code

```cython
cdef extern from "headerfile.h":
    cdef struct struct_name "namespace::stuff":
        pass
```

don't use `cdef cppclass`


# no suitable method found

`cpp/networkit/core/glist.h`: 

```c++
namespace NetworKit{
  namespace core {
      // struct def
      struct CoreComponent {
        std::unordered_set<index> nodes;
        std::unordered_set<index> usable;
        CoreComponent()
        {

        }
      };
  }
}
```

```cython
cdef extern from "cpp/core_maintenance/glist.h":
        # declare the struct
        cdef struct _SubCore "NetworKit::core::GLIST::CoreComponent":
                pass

cdef class Glist:

        cdef vector[_SubCore] *_sc_list

        def __cinit__(self):
		cdef count num_nodes = 10
		self._sc_list = new vector[_SubCore](num_nodes)  # error here
```

the reason:

> `count` is not recognized by Cython as a feasible parameter type to `vector`
