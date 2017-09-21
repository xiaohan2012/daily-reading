# three problems

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

## common pattersn

1. $`P(0)=0`$
2. $`P(N)=1`$
3. $`P(x)=1/2 P(x-1) + 1/2 P(x+1)`$, if $`0 \le x \le N`$

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