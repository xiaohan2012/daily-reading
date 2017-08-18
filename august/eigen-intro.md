# first problem -- solve linear differential equation

suppose there exists two functions on `t`: `v(t)` and `w(t)` and their relationships w.r.t their derivatives, and their value at `t=0`, `v(0)=8, w(0)=5`

$`\frac{dv}{dt} = 4v(t) - 5w(t)`$

$`\frac{dw}{dt} = 2v(t) - 3w(t)`$

the question is: **then what's exactly `v(t)` and `w(t)`?**

to represent in matrix form, denote:

- `u(t) = [v(t) w(t)]`
- $`\frac{du}{dt} = [\frac{dv}{dt} \frac{dw}{dt}]`$

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

1. `x` is in the **null space** of $`A - \lambda I`$
2. $`\lambda`$ needs to make $`A - \lambda I`$ **singular**

the singular matrix satisfies the following

$`\text{det}(A - \lambda I)=0`$

which gives a polynomial whose roots are the eigen values $`\lambda`$.

for each root, we solve one linear equation, in which the solution `x` is called eigenvector. 

together, the form the null space of $`A-\lambda I`$, such space is also called **eigenspace**.

in summary, steps are:

1. find the polynomial by $`\text{det}(A - \lambda I)=0`$
2. find the roots $`\lambda`$
3. for each root, solve $`(A - \lambda I)x=0`$

note if eivenvalue is zero, if means `A` is singular.

# back to the first question

by solving the above equations, we get two pairs of eigenvalue and eigenvector:

- $`\lambda_1, x_1`$
- $`\lambda_2, x_2`$

the complete solution for $`\frac{du}{dt} = Au`$ is given by:

$`c_1 e^{\lambda_1 t} x_1 + c_2 e^{\lambda_2 t} x_2`$ (obvious, right?)

where $`c_1`$ and $`c_2`$ are arbitrary. 


taking into account the initial condition, we need to solve:

$`c_1 x_1 + c_2 x_2 = u(0)`$

just a linear equation, trivial.

note that `x_1` and `x_2` may not be orthogonal

# interpreting eigenvalue

think about $`u=e^{\lambda t} y`$:

- if $`\lambda>0`$, then `u` **increases** exponentially with `t`
  - the larget the $`\lambda>0`$, the faster it grows
- if $`\lambda=0`$, then `u` is constant
- if $`\lambda<0`$, then `u` **decreases** exponentially with `t`
  - the smaller the $`\lambda>0`$, the faster it shrinks

so one way to interpret it is: the **rate of growth/decay**

# computing eigenvalues

to make it diagonal or upper-triangular. 

- for such matrices, the eigenvalues are just on the diagonal

LU-factorization does not work here because row operation changes the eigen values.

however, no explicit formula to do that for `n>5` (because no explict formula for the solution of order-5 polynomials)

## properies of eigen values

1. sum of eigenvalues = trace of matrix
   - trace = sum on diagonal entries
2. product of n eigenvalues = determinant

pivot, diagonal entries and eigenvalues are usualy completely different, except for upper-triangular matrices

## prove that product of n eigenvalues = determinant

by definition of eigenvalues (root of characteristic polynomial):

$`det(A-\lambda I) = \prod_i (\lambda - \lambda_i)`$

by setting $`\lambda=0`$, we get:

$`det(A) = \prod_i \lambda_i`$



# learned

- motivation of eigenvalue/vector from the perspective of sovling linear differential equation
  - in core: exponential function
- mathematically, eigenvalue makes $`A-\lambda I`$ singular and eigenvector is simply in nullspace of $`A-\lambda I`$ 
- how to find eigenvalues/vectors using characteristic polynomial (defined by determinant)
- interpretation of eigenvalue: rate of decay/growth