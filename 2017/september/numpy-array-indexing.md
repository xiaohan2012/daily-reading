

```python
import numpy as np
```

# single element indexing


```python
x = np.arange(10)
print(x[2])  # 2
print(x[-2]) # 8
```

    2
    8



```python
x2d = x.reshape((2, 5))
print(x2d[0, 1])  # 1
print(x2d[1, 1])  # 6
```

    1
    6


# strides and ranges


```python
print(x[2:5])  # [2, 3, 4]
print(x[:-7])  # [0, 1, 2], -7 is 3 in this case
print(x[1:7:2])  # [1, 3, 5], 1 to 6 at a step size of 2

```

    [2 3 4]
    [0 1 2]
    [1 3 5]



```python
# block sub-matrix
print(x2d[:, ::3])  # [[0, 3], [5, 8]]
```

    [[0 3]
     [5 8]]


# indexing using arrays


```python
print(x[np.array([7, 5, 3, -1])])  # 7, 5, 3, 9
print(x[[7, 5, 3, -1]])  # the same, 7, 5, 3, 9


```

    [7 5 3 9]
    [7 5 3 9]



```python
# interesting happens
# relevant: https://stackoverflow.com/questions/46116568/numpy-array-indexing-list-index-and-np-array-index-give-different-result/46116736#46116736
x = np.arange(10)
idx = np.array([[0, 1], [1, 2]])  # just list gives IndexError

# equal to [[x[0], x[1]], [x[1], x[2]]]
print(x[idx])  #[[0, 1], [1, 2]]
```

    [[0 1]
     [1 2]]


# indexing multi-dimensional arrays


```python
y = np.arange(35).reshape(5,7)
print(y)
```

    [[ 0  1  2  3  4  5  6]
     [ 7  8  9 10 11 12 13]
     [14 15 16 17 18 19 20]
     [21 22 23 24 25 26 27]
     [28 29 30 31 32 33 34]]



```python
# in comparison to "block matrix"
# this is more discrete
rows = [0, 1, 2]  # indices on first dim
cols = [0, 1, 2]  # indices on second dim, length must match rows (after broadcast)
print(y[rows, cols])  # 0, 8, 6
```

    [ 0  8 16]



```python
# broadcast example
print(y[[0, 1, 2], 1])  # [1, 8, 15], 1 is broadcast to [1, 1, 1]
```

    [ 1  8 15]



```python
# partial index
print(y[[0, 2, 4]])  # takes row 0, 2, 4
print(y[:, [0, 2, 4]])  # takes column 0, 2, 4
```

    [[ 0  1  2  3  4  5  6]
     [14 15 16 17 18 19 20]
     [28 29 30 31 32 33 34]]
    [[ 0  2  4]
     [ 7  9 11]
     [14 16 18]
     [21 23 25]
     [28 30 32]]



```python
# image look-up example
cm = np.array([[0, 0, 0], [1, 1, 1], [2, 2, 2]])  # assume it's an integer-to-RGB table

# the actual image, with each element being the color id
img = np.array([[0, 1], [1, 2]])

# using the map, we get the RGB version of image
print(cm[img])

# interpreted as [[cm[img[0,0]], cm[img[0, 1]]], [cm[img[1, 0]], cm[img[1, 1]]]]
print('\nequivalent to:\n')
print(np.array([[cm[img[0,0]], cm[img[0, 1]]], [cm[img[1, 0]], cm[img[1, 1]]]]))
```

    [[[0 0 0]
      [1 1 1]]
    
     [[1 1 1]
      [2 2 2]]]
    
    equivalent to:
    
    [[[0 0 0]
      [1 1 1]]
    
     [[1 1 1]
      [2 2 2]]]


# indexing using boolean array


```python
# the mask
b = y>20
print(b)
```

    [[False False False False False False False]
     [False False False False False False False]
     [False False False False False False False]
     [ True  True  True  True  True  True  True]
     [ True  True  True  True  True  True  True]]



```python
# b and y have the *same* dimension
y[b]  # returns a 1-d array
```




    array([21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34])




```python
b5 = b[:, 5]
print(b5)

# b5's dim < y.dim
print(y[b5])  # takes the 3rd and 4th row

# equal to y[b5, :]
y[b5, :]
```

    [False False False  True  True]
    [[21 22 23 24 25 26 27]
     [28 29 30 31 32 33 34]]





    array([[21, 22, 23, 24, 25, 26, 27],
           [28, 29, 30, 31, 32, 33, 34]])




```python
# more dimension
x = np.arange(30).reshape(2,3,5)
print(x)
```

    [[[ 0  1  2  3  4]
      [ 5  6  7  8  9]
      [10 11 12 13 14]]
    
     [[15 16 17 18 19]
      [20 21 22 23 24]
      [25 26 27 28 29]]]



```python
b = np.array([[True, True, False],   # (0, 1, :), (0, 2, :) yes
              [False, True, True]])  # (1, 1, :), (1, 2, :) yes
print(b)  # shape (2, 3)
x[b]
```

    [[ True  True False]
     [False  True  True]]





    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [20, 21, 22, 23, 24],
           [25, 26, 27, 28, 29]])



# ... syntax


```python
z = np.arange(81).reshape(3,3,3,3)
z[1,...,2]  # equal to z[1,:,:,2]
```




    array([[29, 32, 35],
           [38, 41, 44],
           [47, 50, 53]])



# dynamic indexing


```python
# now the index depends on variable...
indices = (1,1,1,slice(0,2))  # same as (1, 1, 1, 0:2)
z[indices]
```




    array([39, 40])



# tuple vs list indexing


```python
z[(1, 1, 1, 1)] # equal to z[1, 1, 1, 1]
```




    40




```python
z[[1, 1, 1, 1]]  # equal to [z[1], z[1], z[1], z[1]]
```




    array([[[[27, 28, 29],
             [30, 31, 32],
             [33, 34, 35]],
    
            [[36, 37, 38],
             [39, 40, 41],
             [42, 43, 44]],
    
            [[45, 46, 47],
             [48, 49, 50],
             [51, 52, 53]]],
    
    
           [[[27, 28, 29],
             [30, 31, 32],
             [33, 34, 35]],
    
            [[36, 37, 38],
             [39, 40, 41],
             [42, 43, 44]],
    
            [[45, 46, 47],
             [48, 49, 50],
             [51, 52, 53]]],
    
    
           [[[27, 28, 29],
             [30, 31, 32],
             [33, 34, 35]],
    
            [[36, 37, 38],
             [39, 40, 41],
             [42, 43, 44]],
    
            [[45, 46, 47],
             [48, 49, 50],
             [51, 52, 53]]],
    
    
           [[[27, 28, 29],
             [30, 31, 32],
             [33, 34, 35]],
    
            [[36, 37, 38],
             [39, 40, 41],
             [42, 43, 44]],
    
            [[45, 46, 47],
             [48, 49, 50],
             [51, 52, 53]]]])



# learned


## array vs list indexing 

if `x, y` are 1-d,  `a[list(x, y)]` and `a[np.array([x, y])` returns the same thing `[a[x], a[y]]`

however, if `x, y` are more than 1-d, for example 2-d, in other words `[[x0, x1], [y0, y1]]`, then they give different results:

- `a[[x, y]]` gives `[a[[x0, x1]], a[[y0, y1]]]`
- `a[np.array([x, y])]` gives `[[a[x0], a[x1]], [a[y0], a[y1]]]`

why this difference?

## index on each dimension

`a[row, col]`, where `row` and `col` are indices for each dimension, the `i`the element in the output is by `a[row[i], col[i]]`


