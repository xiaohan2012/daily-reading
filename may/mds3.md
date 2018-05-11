# matrix multiplication

assume M has m rows and N has n columns.

## map

for M

```
for i in 1...m
    for j in 1...n
       emit ((i, j), M[i, :])
```

for N

```
for j in 1...n
    for i in 1...m
       emit ((i, j), N[:, j])
```


## reduce

for each `((i, j), [M[i, :], N[:, j]])`, return `((i, j), dot(M[i, :], N[:, j]))`, where `dot` is dot product

what if one row in M or one column in N cannot fit into memory of a single machine

not sure if single pass is ok. but the idea is split the row/column into `k` strides, 
but need to sum up the value from each stride. 


# communication cost

denote size in R(A, B), S(B, C) and T(C, D) as m, n and k

## For L

communication cost for R(A, B) x S(B, C): 

- input for map: m + n (for each record)
- input for reduce: m + n (for each record)

so in total: 2(m+n)

denote there p records being output by the above operation. 

for then RS(A, B, C) x T(C, D)

- input for map: p + k
- input for reduce: p + k

in total, the cost is: m + n + p + k

## for R

similarly, the cost for S(B, C) x T(C, D) is n + k

and assume there are q output records in ST(B, C, D), the cost for R(A, B) x ST(B, C, D) is m + q

in total, it takes m + n + q + k.

so the relative advantage of L or R is detemrined by the relation between p and q. 

if p > q, then use R,
o/w, use L



