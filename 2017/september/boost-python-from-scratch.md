# source code

```c++
char const* greet()
{
  return "hello, world";

}

#include <boost/python.hpp>

BOOST_PYTHON_MODULE(hello) // the import name in Python!!!
{
  using namespace boost::python;
  def("greet", greet);
}
```

in python

```python
import hello
print hello.greet()
```


# compiling

```
g++ -c hello.cpp -fPIC  -I /usr/include/python3.5/
```


- `-fPIC`: PIC addressing (position independent coding)

- `-I /usr/include/python3.5/`: where to look for the header file
  - this is necessary because boost-python depends on it

- boost headers are already in the default dirs. so it's not shown here

# linking

the command:

```
g++ -shared -Wl,--export-dynamic hello.o -L/usr/lib/x86_64-linux-gnu/ -lboost_python-py35 -o hello.so
```

- `-L` tells the linker where to find the dynamic library files (`.so` files)
  - usually it's `/usr/lib/`, but in my computer, it's `/usr/lib/x86_64-linux-gnu/`. 

- `-l` tells the library name: in our case, `boost_python-py35`. it's actual name is `libboost_python-py35.so.1.58.0`. I guess the suffix `.so.1.58.0` can be dropped

- `-Wl,--export-dynamic`:the `-Wl` tells to send `--export-dynamic` to linker `ld`

- `-shared`: produce a shared object which can then be linked with other objects to form an executable

# others

- `locate` in ubuntu to find file
- `-I`: header file directory
- `-L`:  library directory
- `-l`: library name

# source

https://shocksolution.com/python-basics-tutorials-and-examples/linking-python-and-c-with-boostpython/