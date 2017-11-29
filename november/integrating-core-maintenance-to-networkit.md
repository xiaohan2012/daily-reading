


# networkit note 

## primitive types

under namespace `NetworKit`

- [typedef ... count](https://github.com/xiaohan2012/networkit/blob/Dev/networkit/cpp/Globals.h#L21)
- [typedef ... node](https://github.com/xiaohan2012/networkit/blob/Dev/networkit/cpp/Globals.h#L23)


# testing

when using `--gtest_filter`, escape `*` by `\*`

for example: `./NetworKit-Tests-Dbg --gtest_filter=\*GlobalGTest\*`


# scons

in `build.conf`:

- `includes`: the directory where `gtest` header files directory lies
  - `/usr/local/include/`, not `/usr/local/include/gtest`
- `lib`: the directory where `gtest` so files lies

# links

- [building googletest using cmake](https://stackoverflow.com/questions/13513905/how-to-setup-googletest-as-a-shared-library-on-linux)
  - not using standard `make install`
  - `ldconfig` to refresh the linker info
- 


# breakpoint

`make main.o` gives 

```
main.cpp:61:27: error: invalid new-expression of abstract class type ‘NetworKit::core::GLIST’
```