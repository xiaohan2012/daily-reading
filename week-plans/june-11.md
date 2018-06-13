# monday

- read the active learning paper
- subgraph function and example in C++ and metis
- spectral clustering
- skim www papers


# tuesday

- metis: read the graph from file and partion
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