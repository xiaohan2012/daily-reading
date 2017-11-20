# Fully Dynamic Algorithm for Top-k Densest Subgraphs

# problem

extract top-k densest subgraphs in edge stream

density is defined by average degree (inside the subgraph)

# main data structure

observation: only nodes with high degree can be contained in dense subgraphs

the idea is maintaining a group of node-disjoint subgraphs (called "snowball"), in which nodes have high degree

the invariant to maintain is:

- each snowball has the maximium core number in its connnected component
- nodes in each snowball are connected 

# update method

to read






