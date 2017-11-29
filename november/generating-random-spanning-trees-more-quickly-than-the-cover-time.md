# generating random spanning trees more quickly than the cover time

https://dl.acm.org/citation.cfm?id=237880

# algorithm

## rooted version

1. intially current tree only contains the root
2. for each node, do random walk until it touches the current 
   - mark all the nodes on the walk as visited and they become part of tree

## unrooted version

randomly select a root with some caveats

# don't understand

- using cycle popping to prove the distribution
- running time proof (hitting time) haven't checked

# learned

some terms:

- cycle popping: a proof technique for the sampling distribution
- loop-erased random walk: random walk that gets rid of loops (by marking visited nodes)

dealing non-stochastic weighted graph:

- normalize the edge weights
- adding cycling to itsself (unrooted version)

# adapting to steiner tree

replace 2 by:

- "for each terminal nodes", instead of "for each node"


however, unable to prove property