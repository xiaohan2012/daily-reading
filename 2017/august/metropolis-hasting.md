http://nonconditional.com/2013/10/understanding-the-metropolis-hasting-a-tutorial/

# goal

sample from stationary distribution using MC

# requirement and challenge

design transition function that satisfies the detailed balance (reversibility), which is a sufficient condition for unique stationary distribution. 

$`\pi(i) T(i, j) = \pi(j) T(j, i), \forall i, j`$

however, such transition function is not easy to find


# approach
 
find some transition $`T`$ that does not satisfy detailed balance, for example

$`\pi(i) T(i, j) > \pi(j) T(j, i)`$

intuitively, $`Pr[x \rightarrow y] > Pr[y \rightarrow x]`$. 

this is against the detailed balance condition. 

we need to increse $`Pr[y \rightarrow x]`$ to match $`Pr[x \rightarrow y]`$

## compensation

we add a "compensation" term $`A(i, j)`$ to make reversibility hold

$`\pi(i) T(i, j) A(i, j) = \pi(j) T(j, i) A(i, j)`$

without loss of generality, assume $`\pi(i) T(i, j) > \pi(j) T(j, i)`$ holds, then


$`A(i, j) = \frac{\pi(j) T(j, i)}{\pi(i) T(i, j)}`$ and $`A(j, i)=1`$ 

makes the above hold.  $`A(i, j)`$ is the acceptance probability. 

in other words, the transition now has two steps:

- $`T(i, j)`$: normal one
- $`A(i, j)`$, compensation if necessary

if $`A(i, j)`$, this process is simply tossing a coin