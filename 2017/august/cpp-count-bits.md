# problem

[statement](https://leetcode.com/problems/counting-bits/description/)

given a number `num`, for each number in `0,...,num`

count the number of 1s in its bit representation.

for example, `num=5` gives `[0,1,1,2,1,2]`

# dynamic programming

denote the dp table as `d`

for number `i`, denote:

- the largest index of its bit 1 as `e`: `3->1`, `7 -> 2`, `8->3`

its number of 1s in bit repr is

`d[i] = d[i-pow(2, e-1)] + pos e-1 on bit repr of i` 

to see why, draw a diagram and find the pattern

# code

```c++
#include <math.h>

vector<int> countBits(int num) {
  vector<int> r(num+1, 0);
  for(int i=0; i<=num; i++){
    if(i<=1){
      r[i] = i;
      continue;

    }
    int e = (int)log2(i);
    int d = (int)pow(2, e-1);
    r[i] = r[i-d];
    if(i&(1<<(e-1))) // (e-1)th bit
      r[i] += 1;

  }
  return r;
}
```

