# three problems: random walk in 1D

random walk in one-dimensional finite network

## drunkard's walk

image a 1-dimension street with $`N+1`$ stops (from 0 to $`N`$) and a drunkard that roams on the street. 

On one end of the street (stop 0), it's the bar, on the other end (stop n), it's the drunkard's home. 

the roaming goes like this:

- if he is at $`1 \le x \le N`$: he has 1/2 of proba to go either left or right
- if he is at $`x=0`$ or $`x=N`$, he stays, the roaming is done.

now the question is:

what's the probability $`P(x)`$ that he vistis $`N`$ before $`0`$ if starting from $`x`$.

Obviously, $`P(0)=0`$ and $`P(N)=1`$. 

## penny matching game

Two people play a game (suppose one is me). At each round, I have 1/2 proba of lossing or gaining one coin. I win if I have $`N`$ coins and loss if I have zero coins.

now the question is:

what's the probability $`P(x)`$ that I win if  start with $`x`$ coins.

Obviously, $`P(0)=0`$ and $`P(N)=1`$.  

## electric network problem

again a line, but electic network, with $`N`$ resistors with resistance $`R`$ (starting from 1 to $`N-1`$). I put 1 voltage on the end, and 0 voltage o the other end. so

- $`v(0)=0`$
- $`v(N)=1`$

question: what the voltage beween $`i`$th and $`i+1`$the resistor?

using Ohm's law: $`i_{xy}=\frac{v(x)-v(y)}{R}`$

using Kirchhoff's law, (in current + out current=0)

$`\frac{v(x-1)-x(x)}{R} + \frac{v(x+1)-x(x)}{R}=0`$

so $`v(x) = 1/2v(x+1) + 1/2v(x-1)`$

they are the same problem. 

## common patterns

1. $`P(0)=0`$
2. $`P(N)=1`$
3. $`P(x)=1/2 P(x-1) + 1/2 P(x+1)`$, if $`0 \le x \le N`$

also applies to $`v`$ of the electric network

remarks:

1. the above is actually a linear system (and it has unique solution)

2. as a generalization, the walk can be biased with probability $`p`$, and it's 
$`P(x)=1/p P(x-1) + (1-p) P(x+1)`$, if $`0 \le x \le N`$

3. there is some relationship between $`p`$ and resitance, $`p=\frac{\frac{1}{R_{x-1}}}{\frac{1}{R_{x-1}} + \frac{1}{R_x}}`$

## more general form: harmonic function

- a set of points: $`S=\{0, 1, \ldots, N\}`$
- interior points: $`D=\{1, \ldots, N-1\}`$
- boundary points: $`B=\{0, N\}`$

a function $`f: S \rightarrow \mathbb{R}`$ is harmonic if:

$`f(x)=\frac{f(x-1)+f(x+1)}{2}`$ for $`x \in D`$ (looks familiar?)

*Dirichlet problem*: given values on boundary points, find a harmonic function on interior points. 

Uniqueness principle: for the same boundary values, harmonic function is unique (proved by maximum. 

Maximum principle: the maximum and minimum of $`f`$ corresponds to $`B`$

in other words, $`f(x)`$ $`D`$ are between $`f(x)`$ on $`B`$. 

**uniqueness proof**: suppose $`h(x)=f(x)-g(x)`$, prove that $`h(x)=0`$ for $`0<x<N`$ using maximum principle (omitted).

the walker will eventually reach either point in $`B`$: proved by maximum principle. 

**exercise** let $`m(x)`$ be the *expected* number of steps to reach either 0 or $`N`$ from $`x`$. then:

1. $`m(0)=0`$ and $`m(N)=0`$ (because it arealy reaches)
2. $`m(x)=\frac{m(x+1)+m(x-1)}{2} + 1`$ (plus 1 because we need to take one more step to reach $`x`$ from its neighbors )

what is the condition for unique solution? note that the maximum principle does not necessarily hold. 

but I think the corresponding linear system is non-singular. 

# random walk in 2D

what is:

1. the probability $`p(x)`$ that the random walker will reach point $`E`$ (escape) before reahcing $`P`$ (meet the police) if he starts at interior point $`x`$
2. or the voltage at interior points $`x`$ is $`P`$ has voltage 1 and $`E`$ are grouneded. 

![](figs/random-walk-in-2d.png)

suppose it has 1/4 probability to one of its 4 neighbouring points. 

harmonic function: 

$`f(a, b) = \frac{f(a-1, b) + f(a, b-1) + f(a+1, b) + f(a, b+1)}{4}`$

using kirchoff's law, $`v(a, b)`$ also satisfies the above. 

maximum principle: harmonic function will always reach its maximum/minimum at its boundaries. 

uniqueness is preserved. 

exercise: 

1. if $`f`$ and $`g`$ are harmonic, then $`h=a \cdot f + b \cdot g`$ is harmonic for constant $`a`$ and $`b`$
   - superposition principle
2. suppose we have $`B_1, \ldots, B_n`$ boundary points and we know the harmonic function $`e_j(a, b)`$ if $`B_j=1`$ while $`B_i=0, \forall i \neq j`$. then suppose the boundary values are $`v_1, \ldots, v_n`$, then harmonic function is $`f(a, b) = \sum_j v_j e_j(a, b)`$
   - proved using the above property

**question**: how to get the solution?

## method 1: monte carlo method

idea: 

- for each $`x`$, simulate $`n`$ experiments
- count the fraction of successes $`\hat{p}`$ as an estimation of the value $`\hat{m}`$
  - denote $`S_n`$ as number of susscess, then $`\hat{p}=S_n / n`$
  - $`q = 1-p`$

disadvantages: if $`p`$ is very small, then according to central limit theorem, to acquire good accuracy $`n`$ needs to be large. 

$`P(-k < \frac{S_n-np}{\sqrt{npq}}<k) \approx A(k)`$

- $`A(k)`$ area under the normal curve between $`-k`$ and $`k`$

estimation method, assume some value of $`k`$ (e.g, $`k=2`$), divide $`S_n`$ and $`np`$ by $`n`$. 

## method 2: dirichlet problem and method of relaxations

dirichlet problem: given a metal square, cut off a small square inside it.

assume the outer boundaries have tempoerature 1 and inner boundaries have temperature 0, what are the temperature of the interior points, $`u(x, y)`$

u(x, y) is harmonic function but in the continuous region.

usually we solve this be discretise it. 

relaxtion method: 

1. for each interior point, adjust its value to be equal to its surroundings
   - this adjustment makes some part equal while also producing other unequal parts
2. repeat the above process until convergence. 

faster than monte carlo method


## method 3: solve by linear equation

each interior point correspond to a variable and a linear equation.

together we solve a linear system

it's exact but needs matrix inverse

## method 4: markov chain

absorbing state: once entered, cannot leave it, like home and bar in the drunkard example

absorbing markov chain: have at least on absorbing state

a random walker on the absorbing markov chain will eventually end up in the absorbing state(s). 

canonical form:

$`\mathbf{P} = \begin{pmatrix} \mathbf{I} & \mathbf{0} \\ \mathbf{R} & \mathbf{Q} \end{pmatrix}`$

- $`\mathbf{I}`$ transition within absorbing states
- $`\mathbf{Q}`$ transition within non-absorbing states
- $`\mathbf{R}`$ transition from non-absorbing states to absorbing ones

fundamental matrix: $`N=(\mathbf{I} - \mathbf{Q})^{-1}`$

- $`\mathbf{N}_{ij}`$: expected number of times we will be in $`j`$ before reaching absorbing states if starting from $`i`$ 
  - for $`N_{11}`$, it starts at iteself, so already 1, it has $`\frac{1}{2} \times \frac{1}{2}`$ probability to go $`1 \rightarrow 2 \rightarrow 2`$ and $`\frac{1}{2}^{4}`$ to go $`1, 2, 3, 2, 1`$, and so on
  - the limiting value is $`3/2`$
  - but why in general (theoretically)? why inverse has such interpretation?
  
- $`t=\mathbf{N} \mathbf{I}`$: expected number of steps for each starting state before absorbtion. (duration of the random walk, if it touches the absorbing state, it terminates)

- $`\mathbf{B}=\mathbf{N}\mathbf{R}`$: probability of ending at each absorbing state given some starting state. 
  - why this is probability?

example for 1-D random walk (5 states):

![](figs/random-walk-matrix-examples.png)


# electric network

## concepts

- each edge $`(x, y)`$ has resistance $`r_{xy}`$ and conductance $`c_{xy}=1/r_{xy}`$

- transition probability $`p_{xy}=\frac{c_{xy}}{c_x}`$, where $`c_x=\sum_y c_{xy}`$ and $`P=\{p_{xy}\}`$ the transition matrix
  - $`c_{xy}=c_{yx}`$ holds
  - $`p_{xy}=p_{yx}`$ does not hold because the denumerator might differ

$`f`$ row vector of length $`n`$: each entry being the probability mass at the node

if $`fP=f`$, then $`f`$ is stationary. 

## $`f`$

$`f_x = \frac{c_x}{c}`$, where $`c=\sum_x c_x`$ is stationary. 

proof:

$`(fp)_y=\sum_x f_x p_{xy}=\sum_x \frac{c_x}{c} \frac{c_{xy}}{c_x}=\frac{c_y}{c}=f_y`$

But, does this mean the stationary distribution is easy to compute? 

## unweighted and undireted case

if the graph is unweighted, then $`c_x=d_x`$, the node degree, $`c=2m`$ and $`f_x=d_x / 2m`$, thus stationary distribution on node $`x`$ is proportional to its degree. 

also, the probability of traversing an edge $`(x,y)`$ in one direction is $`\frac{d_x}{2m} \frac{1}{d_x}=\frac{1}{2m}`$ (uniform)


## weighted case
probability of traversing edge $`xy`$ and edge $`yx`$ is the same

due to the fact that $`c_{xy}=c_{yx}`$

![](figs/electric-symmetric-edge-probability.png)


# harmonic function

- $`g`$: value function mapping node to real number value
- boundary vertices: vertices with value fixed (like labeled instances)
- interior vertices: vertices with flexible values, which equals weighted average of values from its neighbors. 

for vertex $`x`$, the weights $`\sum_y p_{xy}=1`$. 

*definition*: $`g`$ is **harmoic** if and only if  $`g_x = \sum_y p_{xy} g_y`$



# source

http://www.cs.cornell.edu/courses/cs4850/2010sp/Course%20Notes/Chap%205%20part%201%20electrical%20networks%20random%20walks.pdf