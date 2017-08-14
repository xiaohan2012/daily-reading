# basics

- check even/odd using bit-wise **and**
  - is even: `x & 1=0`
  - is odd:  `x & 1=1`
- **xor**:
  - `x ^ y`
- **not**: `~x`, all bits inverted
- `x << k`: append `k` zeros to the right
  - left shift
- `x >> k`: remove last `k` bits  (on the right)
  - right shift

# applications

## access `k`th bit of `x`: `x & (1 << k)`

print out bit representation

for each position `k`:

- print `1` if `x & (1 << k)` is not zero
- print `0`, otherwise

## set `k`th bit to 1

`x = (x | (1 << k))`

## set `k`th bit to 0

`x = (x & ~(1 << k))`

example: 

- `k=4`
- `1 << k`: `010000`
- `~(1 << k)`: `101111`

## inverts `k`th bit

`x = x ^ (1<<k)`

cool!


## set operation

each bit represents whether an element is in or not:

- insersection: `x & y`
- union: `x | y`
- set difference: `x & (~y)`
- complement: `~x`

## all subsets

each bit represents whether an element is in or not

```c++
for(i=0; i<(1<<n); i++){
    // process subset i
}
```

## all subsets of size `k`

add statemetn: `if __builtin_popcount(b) == k`


# iterate permutation using dynamic programming and subset

## example 1

for numbers `1...n`, count the number of permutation s.t. each consecutive numbers' absolute difference is larger than 1.

denote `f(S, i)` as the number of such permutations ending on `i` on set `S` (note that `i` belongs to `S`.

then the substructure is:

`f(S, i)=\sum_{j \in S -{i} && |j-i|>1} f(S-{i}, j)`

```c++
int count(int n){
  int t[1<<n][n];

  // to initialize all entries to zero
  // key
  REP(i, 0, (1<<n)-1)
    REP(j, 0, n-1)
      t[i][j] = 0;

  REP(i, 0, n-1) // f({i}, i)=1
    t[1<<i][i] = 1;

  REP(s, 0, (1<<n)-1){
    REP(i, 0, n-1){ // s ending in i
      REP(j, 0, n-1){ // s-{i} ending in j
        if((s&(1<<j)) && (s&(1<<i)) && (abs(i-j)>1))
          t[s][i] += t[s^(1<<i)][j];
      }
    }
  }
  int r = 0;
  REP(i, 0, n-1)
    r += t[(1<<n)-1][i];
  return r;
}
```
       
