# monte carlo integration

problem: compute $`I=\text{E}_f w(x) = \int_a^b f(x)w(x) dx`$, where:

- $`f(x)`$ is some density function with domain $`[a, b]`$

MC method:

1. sample $`N`$ points $`\{x_i\}`$ from distribution $`f(x)`$
2. approximate $`I=\frac{1}{N} w(x_i)`$

intuition: 

- if we sample enough data points $`\{x_i\}`$ from $`f(x)`$, then the frequency for each unique value $`x_i`$ should be proportional to $`f(x_i)`$
- note that $`f(x) dx`$ in the integration matches to $`frequency(x) \frac{1}{N} `$ in the approximation form
- if $`N`$ is large enough, it converges to the true value

## example: Gaussian CDF

problem: calcualte $`\text{E}_N \text{1}(X \le a)`$, where:

- $`\text{1}(X<a)`$ is indicator function of wheter $`X \le a`$ holds
- $`N \rightarrow N(0, 1)`$ is Guassian distribution centered at 1 with std $`1`$

in other words, we want to calculate $`Pr(X \le a)`$

then using monte carlo integration, we sample $`N`$ points $`\{x_i\}`$ from $`N(0, 1)`$ and approximate by:

$`I=\frac{\sum_i \text{1}(x_i \le a)}{N}`$
