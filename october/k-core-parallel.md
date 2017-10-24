# Core Maintenance in Dynamic Graphs: A Parallel Approach based on Matching

# main idea

insert a matching of edges in parallel because such way guarantees that node core number change is at most 1. 

# concepts

available set of edges: edges that will cause node core number change to be at most 1. 

edge core number: core number of the higher end point

matching of a set of edges: if each pair of edge do not have any common endpoint. 

k-matching: if the edges in the matching have the same core number, `k`

k-path-tree of `u`: like the k-shell (connected and same core number), `T_k^{G^{'}}(u)`

exPath-Tree: union of k-path-trees given the nodes in a set of inserted edges 


# main theorems

**lemma 4**: when inserting a matching into the graph, the core number of every vertex can increase by at most one. 

deletion is similar.

# questions

- why "change by at most one" is a necessary condition for parallel processing?

the main point is: knowing how much the core number will change is necessary for core maintenance. 

one happens to be the easiest case. 

this does not prevent considering other amount of changes. 

