# inapproximability intro

- http://courses.csail.mit.edu/6.890/fall14/lectures/L10.html (here)
- [example  problems and their approximability classes](http://courses.csail.mit.edu/6.890/fall14/lectures/L10_images.pdf)
  - set cover $`log(n)`$ while maximum coverage $`O(1)`$
  - independent set $`\Omega(n^{1-\epsilon})`$, really hard

# NP optimization problems

problems such that:

- instances and solutions can be verified in $P$
- cost function in $P$
- decision problem in $NP$
  - difference between $P$ and $NP$: $P$ solvable in poly time while $NP$ only verifiable in $P$

# approximation classes

## PTAS (polynomial-time approximation scheme)

- additional input: $`\epsilon`$ (for example, the error bound)
- solution is $`(1+\epsilon)`$-approximation
- **polynomial time** for every fixed $`\epsilon`$

can refer to NP optimization problems with PTAS

## F-APX

NP optimization problems having poly-time $`f(n)`$-approximation for some $`f \in F`$, where $`F`$ is function classes

## APX

-  O(1)-APX
- $`f`$ is constant function 
- **includes PTAS** but is not equivalent

## Log-APX

$`O(\log n)`$-APX

## Poly-APX

$`n^{O(n)}`$-APX

# approximation preserving reductions

basic flow:

given problem A and B

- convert instance $`x`$ of A to instance $`x^{'}`$ of B
- find solution $`y^{'}`$ of B
- convert $`y^{'}`$ to $`y`$ for $`x`$

## PTAS reduction

purpose: to prove whether my problem is PTAS or is not

$`\forall \epsilon >0, \exists \delta=\delta(\epsilon)>0 `$ s.t. $`y^{'}`$ is $`(1+\delta(\epsilon))`$-approximation to B, then $`y`$ is $`(1+\epsilon)`$-approximation to A. 

**question**: what's the `\delta` function?

in other words: 

- $`B \in PTAS \rightarrow A \in PTAS`$
  - this is used to prove `A` is PTAS (`A` is our problem)
- $`A \not\in PTAS \rightarrow B \not\in PTAS`$ (logic axiom)
  - if we know `A` i not PTAS, and we have the above reduction, then we can prove `B` is not PTAS
  - in this case, `B` is our problem

- also true for APX

note on $`\delta(\epsilon)`$

it's a function of $`\epsilon`$. it might be  small. 

**BP**

## AP-reduction

if $`\delta(\epsilon)=O(\epsilon)`$ (linear in $`\epsilon`$, no growth assumption). 
then $`B \in O(f)\text{-}APX \rightarrow A \in O(f)\text{-}APX`$ 

## strict reduction

$`\delta(\epsilon)=\epsilon`$ 

**BP: 36:00**


# further

- http://courses.csail.mit.edu/6.890/fall14/lectures/L11.html
- http://courses.csail.mit.edu/6.890/fall14/lectures/L12.html
