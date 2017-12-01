# generating random spanning trees more quickly than the cover time

https://dl.acm.org/citation.cfm?id=237880

# algorithm

## rooted version

1. intially current tree only contains the root
2. for each node, do random walk until it touches the current 
   - mark all the nodes on the walk as visited and they become part of tree

## unrooted version

randomly select a root with some caveats



# cycle popping proof

it's a different algorihm on surface but essentially identical to the loop-erasing algorithm (not sure why)

## equivalence of cycle popping and LERW

- random walk is defined by the stacks and their top elements. 
- we start with some vertex, do a random walk using the stacks. 

if we re-visited vertex (cycle encountered), we pop the cycles on that path until no cycles exist, then we redo the random walk from the same vertex. 

we repeat the above random walk until the walk touches the current tree (initially the root) and we add the visited nodes and edges to the current tree. 

then we switch to another unvisited node. 
  
## main idea

- each non-root node is a associated with a stack with its neighbors (randomly generated
- on top of each stack, it defines an directed edge. together, all edges define a directed graph
- the graph can be a spanning tree or contains cycles

if it contains cycles, pop the stacks associated with the cycle. continue the cycle popping until non cycle is found. 

## main theorems

1. if the graph contains a spanning tree, cycle popping is done in finite steps. otherwise, it never terminates. 
2. the probability of the tree generated is uniform. 

## proof for termination within finite number  (assuming it has a spanning tree)

main lemma: every cycle will be eventually popped regardless of the popping order. 

## proof of probability distribution

the cycle being popped is independent with the tree be generated. 

## infinite number of cycles

example: disconnected components


# learned

some terms:

- cycle popping: an algorithm as well as proof technique for the sampling distribution
- loop-erased random walk: random walk that gets rid of loops (by marking visited nodes)

dealing non-stochastic weighted graph:

- normalize the edge weights
- adding cycling to itsself (unrooted version)


# what's missing

- running time analysis (hitting time)

# links 

- http://www.bigredbits.com/archives/226
- http://staff.utia.cas.cz/swart/present/UST.pdf (maybe I should go through it)