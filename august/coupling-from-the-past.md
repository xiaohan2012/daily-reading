# resources

- lecture 7 note: hard to understand the motivation actually
- [video](https://www.youtube.com/watch?v=8jU5tpoS7VE): with good illustrations
- [slides](http://www.cs.tau.ac.il/~amnon/Classes/2010-Seminar-Random-Walk/Presentations/Propp-Wilson.pdf): haven't read yet
- paper: how to get perfectly random sample ...

# goal

two goals:

- perfect sampling: repects the desired distribution
- automatic termination:  determines when the chain stops automatically

because of problems with many MCMC methods (for example, Gibbs sampler)

- approximate sampling
- upperbound not easy to find

# main idea

- coupling: two chains *couple* if they arrive at the same state at some time $`t`$

## coupling from the past

1. prepare chain length $`N1, N2, ...`$ (increasing order, usualy $`2^i`$)
2. simulate a set of chains for length $`Ni`$ from time $`-Ni`$ to time 0 (from the past)
  - $`i=1`$ intially
3. if states at time 0 coaelsced, output the sample
4. otherwise, increment $`i`$

note that:

- random uniform numbers are re-used across all runs
  - aka "coupling"
  - different to forward approach
- for example: simulation from -N_i+1 reuses result between time -N_i to 0.
- [another example](https://youtu.be/8jU5tpoS7VE?t=7m3s)

## main theorem

theorem: the output has the *same* distribution as $`\pi`$

# challenges

- efficiently evaluating if the chains coalesed (because state space is usually exponential)

- how to pick coupling so that the time to terminate is small

# example: ising model

utilizes partial ordering (aka sandwiching technique)

- define configuration order (partia) A >= B if for all $`e \in E`$, $`A(e) >= B(e)`$
- only need to evaluate two chains (max and min)

# remarks of the paper (how to get a perfectly...)

3 ingredients for CFTP:

1. procedure for randomly generating maps: how is the state transition done?
   - a concrete materialization of the random mapping
   - $`RandomMap`$ outputs such materialization 
2. a method of composing random maps: essentially, function composition
   - each random map is a function
     - compoition of random maps: $`f_1 \circle f_2, ..., f_n = f_1(f_2(...f_n(...)))`$
3. a test to determine if a composition of random maps is collapsing
   - whether the composition sends every state to the same state

## two conditions

1. $`f_{0} \circle f_{-1}, ..., f_{-t}`$ converges to constant function with positive probability
   - how to make it happen?
2. $`f`$ preserves the stationary distribution

## coupling from the past VS coupling from the future 

- past: $`F_{-t}^0 \circle f_{-t-1}`$
  - add to right
  - know the future because living in the past
- future: $`f_{t+1} \circle F_0^t`$
  - add to right
  - oblivious of the future because living in the present

implication:

- "past" gives constant function after certain iterations with **probability 1**
- "future" gives constant function after certain iterations with **probability 0**
- not sure why

# learned

- how coupling from the past work
- its usefulness: perfect sampling and automatic stop
- idea of sandwiching: instead of running all states, run only the top and bottom ones
  - if both chains coalecsed, other chains coalecsed as well
  - requires some "ordering"
  - chain in higher state cannot cross a chain in lower state
- once the chains coalesce:
  - it's fine to throw away the previous states
  - continue the evolution and collect all output samples (the chains already mixed to the stationary distribution)
  
# further questions

1. proving the main theorem: when all chains reach at the same state, the output sample is from the desired distribution?
   - in other words, why when the algorithm terminates, the chain reaches equilibrium. 
   - or explain the equivalence between definition of stationaryity $`P \pi=\pi`$ and chain collapsing?
   - a more general question, how to determine if a chain mixes?
2. how to prove the termination time (within finite time)?
   - like the one for ising model in the lecture note
3. how to design such chain (preserving the desired distribution, irreducible and aperiodic)?
4. why and when sandwiching techniques work?
