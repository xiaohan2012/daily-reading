# Core Maintenance in Dynamic Graphs: A Parallel Approach based on Matching

# main idea

insert a matching of edges in parallel because such way guarantees that node core number change is at most 1. 

# concepts

available set of edges: edges that will cause node core number change to be at most 1. 

edge core number: core number of the higher end point

matching of a set of edges: if each pair of edge do not have any common endpoint. 

k-matching: if the edges in the matching have the same core number, $`k`$

k-path-tree of $`u`$: like the k-shell (connected and same core number), $`T_k^{G^{'}}(u)`$

exPath-Tree: union of k-path-trees given the nodes in a set of inserted edges 
  - are the nodes that may change their core number


# main theorems

**lemma 4**: when inserting a matching into the graph, the core number of every vertex can increase by at most one. 

intuition: the degree for each node is increased by at most 1, therefore their core number is increased by at most 1. 

deletion is similar.

# algorithm

two steps:

1. split the edges into matchings: coloring the edges such that no two edges sharing the common endpoint have the same color
2. process each matching sequentially. at each iteration, edges are processed in parallel.

For step 2, edges with the same core number are processed by the same processor (I thought about this) to reudce duplicated processing. the algorithm is based on DFS. 
    - corresponding to Algorithm 2 (essentially the TRAVERSAL algorithm of the VLDB paper, Algorithm 5)



## time complexity

- sequantial: number of inserted/deleted edges
- parallel: maximum number of inserted/deleted edges adjacent to one of the nodes. 

# questions

- why "change by at most one" is a necessary condition for parallel processing?

the main point is: knowing how many the core number will change is necessary for core maintenance. 

1 happens to be the easiest case. 

this does not prevent considering other amount of changes. 

