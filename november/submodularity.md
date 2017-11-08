# basics

- objective function $`f: 2^n \rightarrow \mathbb{R}`$
- goal: select some $`S \in \mathcal{S}`$ such that $`f(S)`$ is minimized/maximized
  - $`S`$ is some solution from solution space $`\mathcal{S}`$

# discrete derivative

an analogy:

$`\delta_x f(S) = f(S + x) - f(S)`$

- $`S \in \mathcal{S}`$
- $`x \in \{e_1, \ldots, e_n\}`$

# submodularity

$`f`$ is *submodular* if for every $`x`$, $`f(S+x)-f(S)`$ is non-increasing as $`X`$ "increases" (or expands)

or 

then if for every $`A \subseteq B`$ and  $`x \not\in A`$

$`f(A+e) - f(A) \ge f(B+e) - f(B)`$

then $`f`$is submodular. 

## equivalence

$`f(A \cup B) + f(A \cap B) \le f(A) + f(B)`$

because 

$`f(A \cup B) - f(A) \le f(B) - f(A \cap B)`$

- $`B \subseteq A \cup B`$
- the added elements are $`B-A \cap B`$


# examples

## coverage function

## cut function

$`\delta(X) + \delta(Y) = \delta(X \cup Y) + \delta(X \cap Y) + |E(X, Y)| + |E(Y, X)|`$

as $`|E(X, Y)| + |E(Y, X)| \ge 0`$, then:

$`\delta(X) + \delta(Y) \ge \delta(X \cup Y) + \delta(X \cap Y)`$

## other examples

- flows to sink: sink is fixed, sources are the input
- max element: maximum value from a set of elements
- entropy
- mutual information 

# minimization vs maximization

minimization is easier than maximization

- minimization can be done in polynomial time (Iwata-Fleischer-Fujishige / Schrijver, 2000)
- while maximization can be NP-hard (max-cut)

## minimization 

can be done via Lovasz extension, turning it into a a convex function

## maximization

if $`f`$ is *monotone* and submodular, then greedy algorithm gives $`(1-1/e)`$-approximation ratio. 

# resource

- https://theory.stanford.edu/~jvondrak/data/submod-tutorial-1.pdf: def of submodularity
- https://courses.engr.illinois.edu/cs598csc/sp2010/Lectures/Lecture20.pdf: examples
- proof of submodularity on cut function: http://melodi.ee.washington.edu/~bilmes/ee595a_spring_2011/lecture1_presented.pdf
