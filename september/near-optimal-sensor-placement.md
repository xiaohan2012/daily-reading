# Near-Optimal Sensor Placements in Gaussian Processes: Theory, Efficient Algorithms and Empirical Studies

**related problem**: predict spatial phenomonon using data from sensors

**real problem**: how to place the sensors

- art gallery problem: how to place guards in a gallery so that all places can be covered by the eye sight. 

traditional approach: 

- dist model: a circle as the eye sight range
  - however, does not model senor very well (due to nosy measurement)
- entropy model: select the places with highest entropy (most uncertainty)
  - however, selected places tend to be at the border
  - plus, entropy is an indirect criterion, not considering the prediction quality of the selected placements.  

this approach: ues mutual information

# Gaussian process

denote the set of variables as $`V \subseteq R^{2}`$

it has: 

1. mean function $`M: R^{2} \rightarrow R`$ 
2. covaraince function (or kernel function) $`K: R^{2} \times R^{2} \rightarrow R`$

just like multi-variate normal distribution but the number of variables is infinite. 

useufulness: 

given $`M`$ and $`K`$, some measurement $`x_A`$ on $`A \subseteq V`$ ($`A`$ is the sensor set), we can predict the value of other variables in $`V`$ (associated with their probability)

for example, we can predict the temperature of other locations

## stationary kernels

usually, $`K`$ is assumed to be stationary, it depends only on the difference, $`K(u, v)=K_\theta(u-v)`$, $`K`$ is parametrized by $`\theta`$. 

isotropic kernels: exponential kernels and gaussian kernels

what is non-stationary kernels like

# sensor placement strategy

## conditional entropy

intuition: minimize condition entropy on the rest of the space *given* the sensors:

$`H(X_{V-A}\mid X_A) = - \int p(x_{V-A} , x_A) \log p(x_{V-A} \mid x_A) d x_{V-A} d x_A`$

note that it's not the same as entropy, more detail on [wikiepdia page](https://en.wikipedia.org/wiki/Conditional_entropy)

objective: $`\text{argmax}_{A \subset V, |A|=k} H(X_{V-A}\mid X_A) = \text{argmax}_{A \subset V, |A|=k} H(X_A)`$
  - because $`H(X|Y) = H(X, Y) - H(Y)`$ 
  - here $`H(X, Y)`$ is a constant

select $`k`$ sensors that minimizes the entropy (uncertainty) on the sensors themself. 

proved to be NP-hard. 

- given $`k`$ sensors, $`A`$, how to evaluate $`H(X_A)`$?

## mutual information criteria

intuition: place sensors that **reduces** uncertainty the most on **the rest** of the space
  - focus on uncertainty reduction, not just uncertainty

goal: $`\text{argmax}_{A \subset V, |A|=k} H(X_{V-A}) - H(X_{V-A} \mid X_A)`$

- in other words, uncertainty before observing - uncertainty after observing

this is the same as [mutual information](https://en.wikipedia.org/wiki/Mutual_information)

## recap on mutual information

two sets of variables, $`A`$ and $`B`$

- entropy: $`H(A)`$ and $`H(B)`$ (like a set)
- joint entropy: $`H(A, B)`$ (like set union)
- conditional entropy: $`H(A \mid B)`$ and $`H(B \mid A)`$ (like set difference)
- mutual information: $`I(A, B)`$ (like set intersection)

relation:

$`I(A, B)`$:

- $`= H(A) - H(A \mid B)`$
- $`= H(B) - H(B \mid A)`$
- $`= H(A) + H(B) - H(A, B)`$
- $`= H(A, B) - H(A \mid B) - H(B \mid A)`$

illustration:

![](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Entropy-mutual-information-relative-entropy-relation-diagram.svg/512px-Entropy-mutual-information-relative-entropy-relation-diagram.svg.png)

# algorithm

maximizing mutual information is NP-hard, but mutual information gain is submodular. 

the standard greedy algorithm can be applied. 

at each step, we choose the sensor $`y`$ that maximizes:

$`MI(A \cup y) - MI(A) = H(y \mid A) - H(y \mid \hat{A})`$

both $`H(y \mid A)`$ and $`H(y \mid \hat{A})`$ can be evaluated in closed form

- Equation 5
- a special property for Gaussian



# resources

- gaussian process: https://www.robots.ox.ac.uk/~mebden/reports/GPtutorial.pdf


# questions

- Gaussian process: how the prediction is done?
- how to speed up to $`O(kn)`$
