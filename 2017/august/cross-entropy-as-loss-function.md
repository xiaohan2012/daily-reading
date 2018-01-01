# introduction

to see why cross entropy is a good loss function, we consider:

- a single neuron with:
  - 1 variable $`x`$, weight $`w`$ and bias $`b`$: $`z=wx+b`$
  - with sigmoid activation function, $`\delta`$
- quadratic loss function: $`1/2 |\delta(z) - y|^2`$
- ground truth: $`x=1, y=0`$

# quadratic loss function

- derivative on $`w`$: $`(\delta(z)-y)\delta^{'}(z))=\delta(z) \delta^{'}(z)`$ by substiting with the ground truth
- derivative on $`b`$: $`\delta(z) \delta^{'}(z)`$

recall the figure of sigmoid function:

- the **larger** the $`z`$, the **smaller** the gradient $`\delta^{'}(z)`$

opposite to the intuition:

- the **bigger** the error (loss), the **more** you learn (gradient)

# cross entropy

## definition

for binary classification: 

$`C(y, a) =y \ln a + (1-y)\ln (1-a)`$

properties:

- if $`y=0`$, the closer $`a`$ is to 0, the smaller the $`C`$
- if $`y=1`$, the closer $`a`$ is to 1, the smaller the $`C`$


## gradient

derivative on $`w`$ is (by some calculation):

$`x (\delta(z)-y)`$

intuition:

- the **larger** the error, the **steeper** the gradient (measured by absolute value), the faster it learns

## cross entropy for more than one neurons

suppose there are $`n`$ neurons, with correct output $`y_1, ..., y_n`$, then:

$`C(y_1, \ldots, y_n, a_1, \ldots, a_n) = \sum\limits_{i=1}^n y_i \ln a_i + (1-y_)\ln (1-a_i)`$

# cross entropy for more than one output classes (multi-class problem)

by def, cross entropy is defined as:

$`H(p, q) = -\sum_{x \in X} p(x) \log q(x)`$

assume $`p`$ is the ground truth distribution and $`q`$ is prediction. 

then $`x \in X`$, there is only one $`x`$ that has $`p(x)>0`$ (actually 1), because it's a multi-class problem. 

- `q` is softmax if `|X|>2`
- if `|X|=2`, then `q` can be either sigmoid or softmax

## cross entropy for sigmoid

`\sum_{i=1, \ldots, L} y \log p + (1-y) \log (1-p)`

in other words, a cross entropy for each label (binary one)

[tensorflow implementation](https://stackoverflow.com/questions/35400065/multilabel-text-classification-using-tensorflow/39472895#39472895)


# source

- [chap3](http://neuralnetworksanddeeplearning.com/chap3.html)
- [hinge loss vs cross-entropy loss](http://cs231n.github.io/linear-classify/#svmvssoftmax)

