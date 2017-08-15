# problem

- given a set $`\mathcal{S}`$ of subsets of `{0..n}`
- for each subset `S`, count the number of sets in $`\mathcal{S}`$ that belongs to `S`

## example

- input `{{0}, {0,2}, {1,4}, {0,1,4}, {1,4,5}}`
- output: `[1, 2, 1, 3, 2]`

for example, `{0, 1, 4}` contains `{0}`, `{1, 4}` and itself

# dynamic programming

denote `f(S, k)` as the number of subsets in $`\mathcal{S}`$ that is equal to `S` minus any elements from `{0...k}`

for example, `f({0,1,4}, 1)=2` because removing 0 gives `{1,4}` and removing nothing gives itself. 

did you see?

- `f({0,1,4}, 1) = f({1,4}, 0) + f({0,1,4}, 0) = f({1,4}, -1) + f({0,1,4}, -1) = 1+1 = 2`

## recursion

for `f(S,k)`:

- `f(S,k-1) + f(S-{k},k-1)` if `k` is in `S`
- `f(S, k-1)` otherise

## efficiency concern

to compute `f(S,k)` we only need `f(*,k-1)`, therefore we need only a 1D array for the DP table.

# code

input: 

- `ss`: set of subsets
- `k`: number of subsets
- `n`: universe size (`n+1`)

```c++
vector<int> count(int ss[], int n, int k){
  vector<int> r(k, 0);

  // important: n+1 (beucase 0...n has n+1 numbers)
  int d[1<<(n+1)];

  REP(i, 0, (1<<(n+1))-1)
    d[i] = 0;

  REP(i, 0, k-1)
    d[ss[i]] = 1;

  REP(i, 0, n){
    REP(s, 0, (1<<(n+1))-1){
      if(s&(1<<i)) //  remove i from s if i in s
        d[s] += d[s^(1<<i)];
    }
  }

  REP(i, 0, k-1)
    r[i] = d[ss[i]];

  return r;
}
```