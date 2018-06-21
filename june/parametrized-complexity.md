# introduction to parameterized complexity

https://www.cs.auckland.ac.nz/courses/compsci750s2c/lectures/introparameterizedcomplexity.pdf

what's the difference between parametrized version and decision version of a problem? for example *set cover*

# notions

- problem instance: $`\Sigma`$
- problem input: $`(x, k) \in \Sigma \times N`$
- language of parametrized problem: $`L \subseteq \Sigma \times N`$, like the set of feasible solutions
- $`L_k`$, $`k`$th slice of $`L`$: $`\{(x, k): (x, k) \in L\}`$

# Fixed Parameter Tractability (FPT)

a problem $`L`$ is FPT if there is an algorithm that *correctly* decides $`(x, k) \in \Sigma \times N`$ if $`(x, k) \in L`$ in time $`f(k) |x|^{\alpha}`$, where:

- $`f(k)`$ is arbitrary, e.g, $`2^k`$
- $`\alpha`$ is constant
- in other words, a polynomial time algorithm that decides if input is feasible

# Parametrized intractability

Barometer of intractability: $`FPT \subseteq W[1] \subseteq W[2] \subseteq W[3] \ldots`$

the larger the $`i`$ in $`W[i]`$, the more unlikely it's FPT

$`W[i]`$ are equivalent in classical complexity theory.

## Parameterized reductions

technique to prove parametrized "hardness"

$`L \rightarrow L^{'}`$ if we can transform $`(x, k) \in L`$ to $`(x^{'}, g(k)) \in L^{'}`$ in time $`f(k) |x|^c`$ s.t. $`(x, k)`$ is feasible if and only if $`(x^{'}, g(k))`$

note that:

- $`f`$ and $`g`$ can be arbitratry function
- $`f(k) |x|^c`$ aligns with the definition of FPT

in contrast to polynomial reduction for NP-completeness proof: 

- for poly reduction, SAT is a common choice
- however for $`W[i]`$ class, it needs a different base problem to reduce to

a common choice for the base problem is **Weighted t-Normalized SAT**

- see the definition of *t-normalized* in the slides


**Proposition**: *Weighted t-Normalized SAT* is complete for $`W[t]`$.

examples: INDEPENDENT SET & CLIQUE are complete for $`W[1]`$

## beyond $`W[i]`$

- $`W[SAT]`$: problems reducible to WEIGHTED SAT.
- $`W[P]`$: problems reducible to WEIGHTED CIRCUIT SAT.

theorem:

$`FPT \subseteq W[1] \subseteq W[2] \subseteq W[3] \ldots \subseteq W[SAT] \subseteq W[P]`$

for the last $`W[SAT] \subseteq W[P]`$ **assumption**, there is no proof.