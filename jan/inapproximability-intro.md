# inapproximability intro

- http://courses.csail.mit.edu/6.890/fall14/lectures/L10.html (here)
- [example  problems and their approximability classes](http://courses.csail.mit.edu/6.890/fall14/lectures/L10_images.pdf)
  - set cover $`log(n)`$ while maximum coverage $`O(1)`$
  - independent set $`\Omega(n^{1-\epsilon})`$, really hard

# approximation classes

## PTAS (polynomial-time approximation scheme)

- additional input: $`\epsilon`$ 
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

$`\forall \epsilon >0, \exists \delta=\delta(\epsilon)>0 `$ s.t. $`y^{'}`$ is $`(1+\delta(\epsilon))`$-approximation to B, then $`y`$ is $`(1+\epsilon)`$-approximation to A. 

in other words: 

- $`B \in PTAS \rightarrow A \in PTAS`$
- $`A \not\in PTAS \rightarrow B \not\in PTAS`$ (logic axiom)


**more about$`\delta(\epsilon)`$**

it's a function of $`\epsilon`$. it might no longer be  small. 

if $`\delta(\epsilon)=O(\epsilon)`$ (linear in $`\epsilon`$, no growth assumption). 
then $`B \in O(f)-APX \rightarrow A \in O(f)-APX`$ (**AP-reduction**)

$`\delta(\epsilon)=\epsilon`$ (**strict reduction**)

**BP: 36:00**


# further

- http://courses.csail.mit.edu/6.890/fall14/lectures/L11.html
- http://courses.csail.mit.edu/6.890/fall14/lectures/L12.html
