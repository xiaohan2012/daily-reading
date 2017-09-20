# learned

- `boost::python::list`: type
- `boost::python::extract<std::string>(..)`: extract value 
- direct interpretation of `python::string` into `std::string`

```c++
class_<World>("World")
    .def("greet", &World::greet)
```

- `std::stringstream`: supports `<<` operator for appending string
- `std::stringstream::str` to get the actual string


# source

https://github.com/TNG/boost-python-examples/tree/master/02-ExposingClasses