# supermodular network games

# concepts

- payoff function
  - or gain for each node
- increasing difference
- supermodular game
  - how to interpret it?
- largest best response mapping
  - maximize self-interest
- pareto prefered
  - order for two states
- largest nash equilibria (NE): x^{*}
  - fixed-point method to compute it

# main results for complete graph

## theorem 4.3 lowerbound for $`x_i^{*}`$: 1

for each core number $`i=1, \ldots, K`$, there exists a threshold $`\gamma_i`$, such that the optimal $`x_i^{*} \ge \gamma_k`$ if $`core(i)=k`$


## theorem 4.3 non-decreasing: 2

given $`x^{*}`$ for $`G=(V, E)`$ and $`y^{*}`$ $`G=(V, E^{'})`$, where $`E^{'} \subseteq E`$, then $`y^{*} \le `$x^{*}$`. 

## upperbound distance to `$\textbf{1}$`: corollary 4.5 

weighted summation of size of shell.

note that `$t_k$` should be `$\gamma_k$` (typo in the paper)

## example for a quadratic payoff

closed form largest NE --> explicit calculation of `$\{\gamma_i\}_{i=1, \ldots, K}$`

# thinking

can we form a problem to maximize the largest NE?

for example: 

- by minimizing the upper bound in corollary 4.5
  - how to compute `$\gamma_k$`?
- or relax the `$\gamma_k$` by any non-decreasing and non-negative number sequence. 
