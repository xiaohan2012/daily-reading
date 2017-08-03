# resources

- lecture 6 note: hard to understand the motivation actually
- [video](https://www.youtube.com/watch?v=8jU5tpoS7VE): with good illustrations
- [slides](http://www.cs.tau.ac.il/~amnon/Classes/2010-Seminar-Random-Walk/Presentations/Propp-Wilson.pdf): haven't read yet

# goal

two goals:

- perfect sampling: repects the desired distribution
- automatic termination:  determines when the chain stops automatically

because of problems with many MCMC methods (for example, Gibbs sampler)

- approximate sampling
- upperbound not easy to find

# main idea

- coupling: two chains *couple* if they arrive at the same state at some time `t`


## coupling from the past

1. prepare chain length `N1, N2, ...` (increasing order, usualy `2^i`)
2. simulate a set of chains for length `Ni` from time `-Ni` to time 0 (from the past)
  - `i=1` intially
3. if states at time 0 coaelsced, output the sample
4. otherwise, increment `i`

note that:

- random uniform numbers are re-used across all runs
  - aka "coupling"
- for example: simulation from -N_i+1 reuses result between time -N_i to 0.
- [another example](https://youtu.be/8jU5tpoS7VE?t=7m3s)

## main theorem

theorem: the output has the *same* distribution as `\pi`

# challenges

- efficiently evaluating if the chains coalesed (because state space is usually exponential)

- how to pick coupling so that the time to terminate is small

# example: ising model

utilizes partial ordering (aka sandwiching technique)

- define configuration order (partia) A >= B if for all `e \in E`, `A(e) >= B(e)`
- only need to evaluate two chains (max and min)

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
2. how to prove the termination time (within finite time)?
   - like the one for ising model in the lecture note
3. how to design such chain (preserving the desired distribution)?
4. why and when sandwiching techniques work?


