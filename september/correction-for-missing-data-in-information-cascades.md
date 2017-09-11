# overview

given an observed cascade, infer the properties of the underlying cascade

- input: observed infections/cascade, graph structure
- output: statistics of the underlying cascades, such as number of infected nodes, number of infected edges, etc..


# notations

- cascade $`C`$
- observed/sampled cascade $`C^{'}`$
- source/root: $`r`$, initially active node
- action sequence $`A=\{(s, t)\}`$, $`s`$ influences $`r`$
- influence cascade $`C_i`$: graph defined by $`A`$ 
  - tree structure
- network cascade $`C_n`$: graph using active nodes and timestmaps only
  - connect to active nodes if they are adjacent and time order is respected
  - source node is unknown ($`(\emptyset, u)`$)
  - DAG structure
- sampled influence cascade $`C_i^{'}`$
- sampled network cascade $`C_n^{'}`$

- $`\mathbf{X}`$ properties of the underlying cascade $`C`$
- $`\mathbf{X}^{'}`$ properties of $`C^{'}`$
- $`\mathbf{X}_{\mathbf{M}}`$: properties of the k-tree cascade
- $`\mathbf{X}_{\mathbf{M}}^{'}`$: properties of the sampled k-tree cascade

other notation:

![](figs/cascade-.png)

# strategy

1. find a sampled k-tree with property $`\mathbf{X}_{\mathbf{M}}^{'}`$ similar to $`\mathbf{X}^{'}`$. 
2. approximate $`\mathbf{X}`$ by $`\mathbf{X}_{\mathbf{M}}`$

The premise is that if $`\mathbf{X}_{\mathbf{M}}^{'}`$ matches $`\mathbf{X}^{'}`$, then $`\mathbf{X}_{\mathbf{M}}`$ will match $`\mathbf{X}`$. 

# (sampled) k-tree

**k-tree**, a model to approximate real cascades. 

parametrized by $`(b, h, k)`$: a balanced tree of height $`h`$ and branching factor $`b`$, each node is augmented with $`k-1`$ edges from its $`k-1`$ closest ancestors. 
- for influence cascade, $`k=1`$ (because tree)
- for network cascade, $`k>1`$ (because DAG)

**sampled k-tree**: $`(b, h, k, p)`$, $`p`$ fraction of nodes being observed. 

# properties in $`\mathbf{X}`$

given sampled k-tree$`(b, h, k, p)`$, the following properties can be calcualted in closed form:

1. number of nodes
2. number of edges
3. number of isolated nodes
4. number of weakly CCs
5. out-degree of a non-leaf node
6. avg node degree

# algorithm

## estimating $`p`$

if $`\sigma`$ is give, $`p=\sigma`$

## estimating $`b, h, k`$

just relying on $`\sigma`$ is problematic (Figure 4)

it uses subsampling to create more data instances. 

not very clear

# questions

- where does it use network structure?

# learned

- contains pointers to real cascades!!
- [code](https://github.com/snap-stanford/snap/tree/master/examples/cascades)

