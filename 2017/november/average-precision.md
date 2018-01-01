# average precision

for a given query, and $`n`$ documents 

- $`y_{true} \in \{0, 1\}^n`$: true labels, binary: relevant or not
- $`y_{pred} \in [0, 1]^{n}`$: predicted probability

then, define $`p(r)`$: precision at recall vallue $`r`$

`$``$math
AP=\int p(r) dr
`$``$

essentially the area under the precision-recall curve.

in discrete space

`$``$math
AP=\sum\limits_{i=1,\ldots,k} P(k) \Delta r(k)
`$``$

suppose there are $`k`$ data points

then **mean average precision**

is just the mean AP over all the queries. 

# mean average precision at $`k`$ (MAP@k)

appeared [here](https://www.kaggle.com/c/expedia-hotel-recommendations#evaluation)

it's the mean of precision at $`i=1, \ldots, k`$

