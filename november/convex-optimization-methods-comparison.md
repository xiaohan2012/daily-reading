# batch SGD

advantages:

- memory efficient compared to full using full data for gradient update
- reduce variance compared to single example SGD

disadvanges:

- choosing learning rate is hard
- global rate applied to all parameters (frequent/rare features)
- trapped in sub-optimal local minimum such as saddle points

# momentum

the current parameter update consists of summation of:

- a fraction of the parameter update from previous step
- gradient of the current step

$`V(t)=\gamma V(t-1) + \alpha \nabla J(\theta)`$

and

$`\theta = \theta - V(t)`$

just like momentum in physics

# Nesterov accelerated gradient

problem with momentum: the "ball" does not slow down when it's near the local minima (due to high momentum, update from previous step).

basic idea:

- make a large jump with the previous momentum
- adjust the position based on the estimated position

# Adagrad

different learning rates for different parameters and it keeps adapting

- make big updates for infrequent parameters and small update for frequent ones. 

- by frequent, it means the gradients are large 
- by infrequent, it means the gradients are small

$`\theta_{t+1,i} = \theta_{t,i} - \frac{\alpha}{\sqrt{G_{t, ii} + \epsilon}} \dot \nabla J(\theta_{t, i})`$

$`G_{t, ii}`$: sum of gradients on parameter $`i`$ until time $`t`$.

why "square" ($`\sqrt`$)?

disadvange:

- learning rate keeps decreasing and eventually close to zero

# Adadelta

adresses the decaying learning rate problem of Adagrad

uses only previous $`w`$ gradients, earlier gradients keep decaying exponentially. 


$`E(g^2)_t = \gamma E(g^2)_{t-1} + (1 - \gamma) g_t^2`$

next replace $`G_{t, ii}`$ in Adagrad by $`E(g^2)_t`$. 

the second version addresses the issue that the gradient are parameter are not of the same unit. 

in this version, $`g`$ is replaced by parameter change $`\Delta \theta`$

# RMSprop

independently deveoped and unpublished. 

- same as first version of  Adadelta 

# Adam (Adaptive Moment Estimation)

store exponentially decaying average of past gradients (momutum), first moment

- in addition to exponentially decaying average of *squared* gradient as in adadelta and RMSprop, second moment
- can be seen as a combination of RMSprop and momentum

replace the $`g_t`$ in update rule in adadelta by modified momentum term. 

- modified because if without modification, they are biased towards zero

# Adamax

# Nadam

Nesterov-accelerated gradient + Adam

# Parallelizing and distributing SGD

## Hogwild!

distributed update of parameter without locking

## Downpour SGD

each machine updates a fraction of the parameters (no sharing, communication)

##  Elastic Averaging SGD



# resources

- http://ruder.io/optimizing-gradient-descent/index.html (more comprehensive)
- https://towardsdatascience.com/types-of-optimization-algorithms-used-in-neural-networks-and-ways-to-optimize-gradient-95ae5d39529f




