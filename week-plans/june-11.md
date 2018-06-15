# monday

- read the active learning paper
- subgraph function and example in C++ and metis
- spectral clustering
- skim www papers


# tuesday

- metis: read the graph from file and partition
- plug it into parabel code

# wednesday

- necessary condition of finding an approximately good median model and the proof
- the non-noise version does not support real-valued node weights, but given the probabilistic nature of cascade model, node weights must be real-valued even the feedback is perfect, how to bridge the gap?
  - what about deterministic cascade model?
- the case for line graph

consider the problem of finding source in probabilitic cascade, 
the user feedback `s^{'}` does not necessarily lie on shortest path from `s^{'}` to `s^{*}`,
so the assumption in Definition 1 does not hold.

on the other hand, the feedback can be considered as "noisy", can we bound the level of noise?

## alternatives

more practical cascade reconstruction

- work on real datasets
- formulate as a supervised learning problem
- use active learning based on graph topology

issues on defining a cascade? reshare cascade? if we know who reshare, we know why are "infected", then what's the effect of re-sample?

- how about the effect of network sampling?

interactively detect controversial/debatable topical cascades?

## discussion: core maximization

- reading on papers that cite the anchored k-core problem
- learning inapproximability
- speed-up of greedy

# thursday

- find some papers on collective classification, think of formulating the cascade reconstruction problem as a collective classification problem
- k-core paper reading
  - create a reading list
  - skim through the papers and add some comments
- parabel

## diffusion prediction over time

general goal: modeling/predicting the popularity of a post

I have read:

- [spikeM, kdd12](../june/spikeM-kdd-2012.md)
- [seismic, kdd15](../june/seismic-kdd15.md)

I have learned:

- self-exciting point process seems to be a popular tool in modeling popularity of diffusion process

what might be interesting:

- can we model the evolution of controversial diffusion process? for example, how does the level of controversy evolve over time



# friday

- cascade reconstruction under realistic cascade models
  - motiation: data acquisition constraint (API limit),  observe only a fraction.
  - considers continous time IC model, but how good is in practice?
