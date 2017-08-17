# first problem -- solve linear differential equation

suppose there exists two functions on `t`: `v(t)` and `w(t)` and their relationships w.r.t their derivatives, and their value at `t=0`, `v(0)=8, w(0)=5`

$`\frac{dv}{dt} = 4v(t) - 5w(t)`$

$`\frac{dw}{dt} = 2v(t) - 3w(t)`$

the question is: **then what's exactly `v(t)` and `w(t)`?**

to represent in matrix form, denote:

- `u(t) = [v(t) w(t)]`
- $`\frac{du}{dt}` = [\frac{dv}{dt} \frac{dw}{dt}]$

and 

$`A = \begin{pmatrix} 4 & -5 \\ 2 & -3 \end{pmatrix}`$

then

$`\frac{du}{dt} = A u(t)`$

with `u(0) = [8 5]`

## single variable case 

solve `du/dt=au` given `u(0)`

pure expoential gives: $`u(t)=e^{at} u(0)`$

## back to original question

suppose `v(t)` and `w(t)` have similar form:

- $`v(t)=e^{\lambda t} y`$
- $`w(t)=e^{\lambda t} z`$

substituting it in gives:


$`\lambda e^{\lambda t} \begin{pmatrix} y \\ z \end{pmatrix} = \lambda e^{\lambda t} A \begin{pmatrix} y \\ z \end{pmatrix}`$

denote `x=[y z]` and canceling out the common terms give us:

$`Ax=\lambda x`$

**what is this?**

note there are two unknowns:

- $`\lambda`$
- $`x`$

so it's not a linear equation, otherwise it would be easy to solve.

# solving $`Ax=\lambda x`$

in other words,  we solve $`(A - \lambda I) x= 0`$. 

this means:

1. `x` is in the *null space** of $`A - \lambda I`$
2. $`\lambda`$ needs to make $`A - \lambda I`$ **singular**

the singular matrix satisfies the following

$`\text{det}(A - \lambda I)=0`$

which gives a polynomial whose roots are the eigen values $`\lambda`$.

for each root, we solve one linear equation, in which the solution `x` is called eigenvector. 

together, the form the null space of $`A-\lambdaI`$, such space is also called **eigenspace**.

in summary, steps are:

1. find the polynomial by $`\text{det}(A - \lambda I)=0`$
2. find the roots $`\lambda`$
3. for each root, solve $`(A - \lambda I)x=0`$




