# random walks and markov chain

https://resources.mpi-inf.mpg.de/departments/d1/teaching/ws11/SGT/Lecture5.pdf

# overview

we talk about undirected graphs

- reversibility and application of it to derive stationary distribution
- fundamental theorem of markov chain (aperiodic and irreducible): no proof
- speed of convergence (related to eigenvalue): no proof


# $`P`$of $`G`$

- unweighted: $`P_{xy} = \frac{1}{\text{deg}(x)}`$
- weighted: $`P_{xy} = \frac{w_{xy}}{\sum_y w_{xy}}`$
- or, $`P=D^{-1}A`$

$`P`$ can be  asymmetric. 

# reversibiliy

> if the $`\pi`$  is reversible, $`\pi_x P_{xy} = \pi_y P_{yx}`$, then $`\pi`$ is stationary distribution for $`P`$, $`\pi P=\pi`$

using this lemma, we can verify the stationary distribution for some graphs. 

- if the graph is unweighted, then $`\pi_x = \frac{\text{deg}(x)}{2|E|}`$
- if $`P`$ is symmetric, then $`\pi_x = \frac{1}{n}`$ (cool! don't know why before)
- if graph is weighted with edge weight $`w_{xy}`$, then $`\pi=\frac{\sum_y w_{xy}}{\sum_{xy} w_{xy}}`$. 

this means for the above graphs, the stationary distribution is easy to compute, avoiding $`O(n^3)`$. 


## calculating $`P^t`$

naive approach, requires $`\log t`$ matrix multiplications

faster approach, decompose $`P=D^{-1/2} N D^{1/2}`$, where $`N`$ is symmatric and can be decomposed into $`R^{-1}DR`$ (orthgonal decomposition)

$`D`$ is the diagonal matrix of $`\pi`$. note that $`\pi`$ is one eigen vector of $`P`$. 

## periodic

$`P`$ is periodic if $`gcd\{P^t_{xx}\}>1`$

or aperiodic if $`gcd(\ldots)=1`$

## irreducibility

there exsits $`t`$ such that $`P^t_{xy}>0`$ for each $`x, y`$

$`x`$ can reach $`y`$ within finite steps. 

intuitively, a connected graph has irreducible markov chain. 

# fundamental theorem

if a markov chain is aperiodic and irreducible, then there exists $`T`$ s.t $`P^{T}_{xy}>0`$

and $`\text{lim}_{t\rightarrow \infty} P^{t}_{xy}=\pi_{y}=\frac{1}{\text{E}[\tau_{y,y}]}`$

$`\tau_{y,y}`$ first time that $`y`$ returns to $`y`$. 

the larger the $`\pi_y`$, the shorter time $`\tau_{y,y}`$ (relates to pagerank)

for $`t \rightarrow \infty`$, each row of $`P^{t}`$ is identical and equals to $`\pi`$. 

# speed of convergence

> $`||x P^t - \pi||_2 \le \lambda^t`$

- $`\lambda=\max\{|\lambda_2|, |\lambda_n|\}`$

for $`d`$-regular graph and symmetric $`P`$ 
