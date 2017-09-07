
# condition number

in the general sense, condition number measures how *sensitive* the answer is to *perturbations* in the input data and to roundoff errors made during the solution process.

for this note: condition number (for matrix inverse) upper-bounds the relative change of linear system $`Ax=b`$ due to change in $`b`$

note that there are more than one condition numbers, for inverse, eigenvalue computation, etc. we consider inverse here. 


# condition number of matrix inverse

matrix euclidean norm, 2-norm of matrix $`A`$, $`||A||`$:

$`M=||A|| = \max \frac{||Ax||}{||x||}`$

in other words, $`M`$ is the **maximum stretch** for a vector $`x`$ after linear transformation over $`A`$

correspondingly, we define the **minimum stretch** (if $`Ax=y`$), 

$`m=\min \frac{||Ax||}{||x||} = \min \frac{||y||}{||A^{-1}y||}=1/\max\frac{||A^{-1}y||}{||y||}`$ = 1/||A^{-1}||


**condition number**: $`\kappa(A)=\frac{M}{m}=||A|| ||A^{-1}||`$

## examples

- for singular matrix:, $`\kappa = \infty`$
- for identity matrix, $`\kappa = 1`$

## exact form

for non-singular matrix, $`\kappa(A)=\frac{|\lambda_{max}(A)|}{|\lambda_{min}(A)|}`$

$`\lambda_{max}`$ and $`\lambda_{min}`$ are the max/min eigen values. 

from [wikipedia](https://en.wikipedia.org/wiki/Condition_number#Matrices)

# how can we use $`\kappa`$?

let's consider linear equation and a small perturbation. 

given $`Ax=b`$, by definition, we known

$`\frac{||Ax||}{||x||} \le M \rightarrow \frac{||b||}{||x||} \le M \rightarrow ||b|| \le M ||x||`$ (1)


suppose we add a small change $`\epsilon`$ to $`b`$ and the resulting new solution is $`x+y`$ (in other words, $`y`$ is the change original solution $`x`$)

note that $`Ay=\epsilon`$ and $`A(x+y)=\epsilon + b`$ both hold. 

by def of $`m`$

$`||\epsilon|| \ge m ||y||`$ (2)

if we measure the **relative change** of $`b`$ and $`x`$, then we use (1) and (2) and have:

$`\frac{||\epsilon||}{||b||} \le \kappa(A)\frac{||y||}{||x||}`$

in other words, the relative change of $`x`$ is upper-bounded by the relative change of $`b`$ and condition number $`\kappa(m)`$. 

the larger the $`\kappa(m)`$, the more sensitive linear system can be. 

# source

https://blogs.mathworks.com/cleve/2017/07/17/what-is-the-condition-number-of-a-matrix/ (with nice formula and explanation)



