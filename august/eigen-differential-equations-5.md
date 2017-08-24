# recap: solution to differential equations

given $`\frac{du}{dt} = A u`$, the solution is a combination of pure exponential solutions:

$`u = \sum_i c_i e^{\lambda_i t} x_i`$

or in matrix form:

$`u = \begin{pmatrix} x_1 && \ldots && x_n \end{pmatrix} \begin{pmatrix} e^{\lambda_1} & \ldots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \cdots & \lambda_n \end{pmatrix} \begin{pmatrix} c_1 \\ c_n\end{pmatrix}`$

