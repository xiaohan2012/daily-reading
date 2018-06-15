# collections

- initialize `unordered_set` by copying from `vector`: `set<int> s(v.begin(), v.end());`, [ref](https://stackoverflow.com/questions/6448967/can-i-copy-vector-elements-in-set-using-the-copy-algorithm)

# string / char array

[assign a string to char array](https://www.geeksforgeeks.org/convert-string-char-array-cpp/): use `c_str` and `strcpy`

# C

```
extern C {
...
}
```

used in C code to make it linkable to C++ program

# compiling/linking/running

- [cannot open shared object file](https://stackoverflow.com/questions/480764/linux-error-while-loading-shared-libraries-cannot-open-shared-object-file-no-s)
- [prevent multiple includes](https://stackoverflow.com/questions/672734/how-to-prevent-multiple-definitions-in-c)
- [mutiple definition error](https://stackoverflow.com/questions/17764661/multiple-definition-of-linker-error)
  - put declarations in `.h` and definitions in `.cpp`