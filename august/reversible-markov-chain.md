- [chap3 of book](https://www.stat.berkeley.edu/~aldous/RWG/Chap3.pdf)
- [lecure note](http://www.math.ucsd.edu/~williams/courses/m28908/scullardMath289_Reversibility.pdf)

# definition

a markov chain is reversible if:

$`\pi_i p_ij = \pi_j p_ji`$ for all $`i, j`$

also called *detalied balance equation*

# two implication

## 1

this implies that:

a chain $`X_1, X_2, ..., X_n`$ has the same distribution as $`X_n, X_{n-1}, ..., X_1`$ (**reversed!**)

proof by showing $`\pi_1 p_12 p_23 ... p_(n-1)n = \pi_n p_n(n-1) ... p_21`$

## 2

if $`\pi`$ satisfies the definition, then $`\pi`$ is *stationary*.

in other words, reversibility implies stationarity.


