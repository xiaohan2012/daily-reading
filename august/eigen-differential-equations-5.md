# recap: solution to differential equations

given $`\frac{du}{dt} = A u`$, the solution is a combination of pure exponential solutions:

$`u = \sum_i c_i e^{\lambda_i t} x_i`$

or in matrix form:

$`u = \begin{pmatrix} x_1 && \ldots && x_n \end{pmatrix} \begin{pmatrix} e^{\lambda_1} & \ldots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \cdots & \lambda_n \end{pmatrix} \begin{pmatrix} c_1 \\ \vdots \\ c_n\end{pmatrix} `$

1. the first matrix is essentially $`S`$
2. the second matrix can be expressed as $`e^{\Lambda t}`$

taken into account initial condition, $`u(0)`$, we have $`u(0)=Sc`$, therefore $`c=S^{-1}u(0)`$ and substituting it back to $`u(t)`$

the final solution is:

$`u(t) = S e^{\Lambda t} S^{-1} u(0)`$

just as $`S \Lambda^k S^{-1} u(0)`$ solves difference equations. 

# matrix exponential

what's the form of $`e^{At}`$, where $`A`$ is a matrix?

recall that the form of $`e^x = 1 + x + x^2/2! + x^3/3! + \ldots`$

the matrix-version has similar form:

$`e^{At} = I + At + \frac{(At)^2}{2!}+ \frac{(At)^3}{3!} + \ldots`$

it should satisfy the properties of exponential such as:

1. $`e^{As} e^{At} = e^{A(s+t)}`$
   - what about $`e^{At} e^{By} ? e^{(A+B)t)}`$?
   - $`t`$ is like the variable, just like $`x`$ in $`e^x`$.
2. $`e^{At} e^{-At} = I`$
3. $`\frac{d}{dt} (e^{At}) = A e^{At}`$

by the 3rd property, we know $`u=e^{At}u(0)`$ is the solution for $`\frac{du}{dt}=Au`$

meanwhile, from the last section, we know $`u=S e^{\Lambda t} S^{-1}`$ is the solution as well. 

then $`e^{At} = S e^{\Lambda t} S^{-1}`$ must hold. 

proof: by diagonalization and def of matrix exp, we have

$`e^{At} = I + S \Lambda S^{-1} t + \frac{S \Lambda^2 S^{-1}}{2!} + \frac{S \Lambda^3 S^{-1}}{3!}  + \ldots = S(I + \Lambda t + \frac{\Lambda^2}{2!} + \frac{\Lambda^3}{3!} + \ldots )S^{-1} = S e^{\Lambda t} S^{-1}`$