# introduction

http://www.geeksforgeeks.org/templates-cpp/

template allows passing **data type as parameter** so we don't need to write functions/classes for different data types. (code re-use)

it works like macro but compiler type checks before template expansion. 

- source code only one class/function
- compiled code might contain mltiple copies of the same class/function with different argument types

# function templates

start with `tempalate<typename T> return_type function_name(args)`

example:

```c++
template <typename T>
T myMax(T x, T y)
{
   return (x > y)? x: y;
}
```

- `T` is the type parameter

call example:

```c++
myMax<int>(3, 7); // T=int
myMax<double>(3.0, 7.0); // T=double
```

# class templates

start with `template <typename T> class class_name{...}`

example:

```c++
// decleration
template <typename T>
class Array {
private:
    T *ptr;
    int size;
public:
    Array(T arr[], int s);
    void print();
};
 
// definition
template <typename T>
Array<T>::Array(T arr[], int s) {
    ptr = new T[s];
    size = s;
    for(int i = 0; i < size; i++)
        ptr[i] = arr[i];
}
 
template <typename T>
void Array<T>::print() {
    for (int i = 0; i < size; i++)
        cout<<" "<<*(ptr + i);
    cout<<endl;
}
```


to use it:

```c++
int arr[5] = {1, 2, 3, 4, 5};
Array<int> a(arr, 5); // T=int
```

# multiple template parameters

```c++
template<class T, class U>
class ...
```

# default value

```c++
template<class T, class U = char>
class A  {
}

A<char> a; //U=char by default
```

# nontype template parameter

```c++
emplate <class T>
void sort(T arr[], int size)
{
    // code to implement Quick Sort
}

sort<string>({string array of size 10}, 10); 
```

does not allow non-constant parameter:

- cannot be parsed at compile time
- [more](https://stackoverflow.com/questions/5687540/non-type-template-parameters)

# template specialization

by default, template function do the **identical** thing for different data types. 

however, we might want some special treatment for certain data types. 

example:

```c++
// A generic sort function 
template <class T>
void sort(T arr[], int size)
{
    // code to implement Quick Sort
}
 
// Template Specialization: A function specialized for char data type
template <>
void sort<char>(char arr[], int size)
{
    // code to implement counting sort
}
```

http://www.geeksforgeeks.org/template-specialization-c/

# template metaprogramming


using templates, we can write programs that do computation at compile time, such programs are called template metaprograms

http://www.geeksforgeeks.org/template-metaprogramming-in-c/

# what is `typename`

clarify what follows is a type. [more](https://stackoverflow.com/questions/1600936/officially-what-is-typename-for)

often, it's interchangeable as `class`

[some diff](https://stackoverflow.com/questions/2023977/difference-of-keywords-typename-and-class-in-templates)