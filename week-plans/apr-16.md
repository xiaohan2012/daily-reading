# week plan

- slides for group presentation
- writing and experiment for core maximization
- how to sample from `\Prod P(u, v)`
  - non-local verion of random walk 
  - probabislistic shortest path
  - probabilistic minimum spanning tree
  - [X] MCMC version of tree sampling
- grading
- apply for more resources from CSC

# monday

- [random steiner tree using MCMC](apr/mcmc-steiner-tree.md)
- [non adjacency edge dependency example(apr/non-adjacency-dependency-example.pdf)


## meeting

- try square loss, l1 loss or cross entropy loss
- try stochastic graph
- larger cascade
- why p2p rises the entropy? 
- why cond-entropy not good on entropy in GRQC?


# Tuesday

- [X] illustration of edge dependency
- todo:
  - [X] [definition of edge-dag, node, edge, dependency](apr/edge-dag-def.pdf)
  - [ ] how to get the set of dependent active edges
  - [ ] update the code

## meeting for core max

- [ ] more graphs
- [ ] random edges (MF creates a bias)
- [ ] candidate = non-edges
- [ ] dense subgraphs: take the dense cores and add edges to the core
  - largest subgraphs such that add k edges and it become and clique
- [ ] for GRQC, does the size-40 clique plays a big role in the objective?
- [ ] why the difference between condmat and grqc? 

- edge_dag: maybe good when the edge order is given