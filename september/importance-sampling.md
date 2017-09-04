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

# importance sampling

## motivation

for mc integration $`\int f(x) w(x) dx`$, if $`f(x)`$ is difficult to sample from, we use this technique

## method

use another distribution $`g(x)`$ which is easy to sample from and re-write the integral

$`\text{E}_f w(x) = \int f(x) w(x) dx = \int f(x) \frac{w(x)}{g(x)} g(x) dx = \text{E}_g \frac{f(x) w(x)}{g(x)} \approx \frac{1}{N} \sum_i \frac{f(x_i) w(x_i)}{g(x_i)}`$

where $`\{x_i\}`$ is drawn from $`g(x)`$ (called **proposal distribution**), instead of $`f(x)`$

## selecting proposal distribution $`g`$

1. $`g`$ should resemble $`f`$
2. $`g`$ should have thick tails 

**bounding $`\frac{f(x)}{g(x)}`$**

intuition for ticker tail, variance has the form $`\int (\frac{f(x) w(x)}{g(x)})^2 dx - \mu^{*}`$

if the term $`\frac{f(x)}{g(x)}`$ is large, $`f(x) \gg g(x)`$, then the variance of the estimation is large. 
so it's reasonable to bound $`\frac{f(x)}{g(x)}`$. 
one way is to ensure $`g(x)`$ does not have regions where $`g(x)=0`$. 
thus thick tail sounds like a good option. 

**avoid undersampling**

suppose we are interested in tail regions that very rare to sample. 
and given limited number of samples, we don't want to under-sample. 
then we use a proposal distribution is has a fat tail at that target region. 

Gaussian tail probability example given in the slides. 

# fat-tailed distribution

compared to normal distribution, fat-tailed distribution has the parts away from the mean are "thicker". 

however, this does not necessarily mean normal distribution is more concetrated than fat-tailed ones. 
it depends on the actual shape of both. 

# source

- [http://astrostatistics.psu.edu/su14/lectures/cisewski_is.pdf](http://astrostatistics.psu.edu/su14/lectures/cisewski_is.pdf)
- [why importance sampling proposal has heavier tails](https://stats.stackexchange.com/questions/76798/in-importance-sampling-why-should-the-importance-density-have-heavier-tails)