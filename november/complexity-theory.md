# sharp-p problems

\#P problems refer to the set of counting problems. 
it asks "how many" rather than "are there any" (decision)

\#P complete problems refer the counting problems that are "hard". 

[examples of \#P complete problems](https://en.wikipedia.org/wiki/Sharp-P-complete)

# decision problem and optimization problem

to prove the NP-hardness of an optimization problem, we can recast it into a decision problem. 

if the decision problem can be solved in polynomial time, then optimization problem can also be solved in poly time (using binary search). 

note that some decision problem can be easy (polynomial time solvable) but the counting problem can be hard. 

# proving \#P-completeness

reduce a \#P-complete problem to the problem at hand. 

if we can prove that by solving our problem, we can solve the problem that is known \#P-complete. then we are done. 

[example](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.302.362&rep=rep1&type=pdf)

# list of \#P-complete problems

- [The complexity of enumeration and reliability problems](http://epubs.siam.org/doi/abs/10.1137/0208032)

# related problems

countings number of s-t simple paths

- arbitrary length: \#P-complete
  - [approximation](http://jgaa.info/accepted/2007/RobertsKroese2007.11.1.pdf)
- length $`k`$: polynomial
  - http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.156.345