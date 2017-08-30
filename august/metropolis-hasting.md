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

*but* we add a compensation term $`A(i, j)`$ to make it equal

$`\pi(i) T(i, j) A(i, j) = \pi(j) T(j, i)`$

in other words, 


$`A(i, j) = \frac{\pi(j) T(j, i)}{\pi(i) T(i, j)}`$

which is the acceptance probability. 

but why do we toss a coin $`u \in [0, 1]`$?