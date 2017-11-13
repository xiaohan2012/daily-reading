# Fast Semidifferential-based Submodular Function Optimization

# background

- [subgradients](https://see.stanford.edu/materials/lsocoee364b/01-subgradients_notes.pdf)
  - gradient is one subgraphdient, but there can be multiple subgradients at some point
- [extreme subgradients](http://www.math.ucla.edu/~wotaoyin/math273a/slides/Lec8_subgradients_of_convex_functions_273a_2015_f.pdf)
  - like the max of all subgradients

# MM framework

use the subgradient to define lower (upper) bound for maxmization (minimization) problems

and minimize (maximize) the upper (lower) bound. 

for minimization problem, the upperbound is:

$`m^{g_Y}(X) = f(Y) + g_Y(X) - g_Y(Y) \ge f(X)`$

and we minimize it.

the paper claims that optimizing $`m^{g_Y}(X)`$ is easier. 

similarly, for maximization, the lowerbound is:

$`m^{h_Y}(X) = f(Y) + h_Y(X) - h_Y(Y) \le f(X)`$

some note:

- Equation 4: $`g_Y`$  is the subgradient of $`f`$ at $`Y`$
  - $`g_Y(X)`$ is just the summuzation of element values  in $`Y`$ indexed by $`X`$ (definition right below Equation 1)
- Algorithm 1: subgradient needs to be picked and the quality of the subgradients determines the convergence speed of the algorithm

