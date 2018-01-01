# Community Search over Big Graphs: Models, Algorithms, and Opportunities

http://www.comp.hkbu.edu.hk/~xinhuang/paper/ICDE-Tutorial17.pdf

# basic setting


given node(s) query, find subgraph(s) that satisfy certian proeprty

1. cohesive community seach: dense (k-core, k-truss
2. attributed community search: graph with attribute
3. social circle discovery: a single node query, find all the circles that the query is in
4. geo-social groups

# applications

- social circle discovery
- planning cock-tail party
- infectious disease control
- tag recommendation
- protein complex identification in protein interaction network

# details

- k-core vs k-truss
  - k-core may have no common friends
  - k-truss must have `k` common friends


# papers

## community search

- Quasi-clique model [Cui et al. SIGMOD’13]
  - single query, find all quasi-cliques
- Query-biased densest subgraph model [Wu et al. PVLDB’15]
- K-core model:
  - Sozio & Gionis KDD’10: a set of querys, + distance, size constraint, maximizing `k`
  - Cui et al. SIGMOD’14: local search
  - Narbieri et al. DMKD’15: min-size community
  - Li et al. PVLDB’15: influential community
- K-truss model: Jonathan Cohen, 2008
  - Huang et al. SIGMOD’14: single query, find all k-truss communities containing `q`
  - Huang et al. PVLDB’16
- Wu et al. VLDB’15: free-rider effect, query-biased densest subgraph
- Huang et al. VLDB’16: closest truss community
  - given a set of query nodes,
  - find k-truss with largest `k` and smalest *diameter*

## attributed community search

- Huang and Lakshmanan, PVLDB’17: attributed graph, set
- Fang et al. PVLDB’16: similar as above

## social circle discovery

- Leskovec and Mcauley, NIPS’12: convex optimization formulation
  - dataset with groundtruth: from snap (fb, g+, twitter
- Uganderet al. PNAS’12: the successrate that this non-existing user will join fb
- Huang et al. VLDBJ’15: top-k structural *diversity* search
  - structural diversity of a node: the number of connected componentsin its ego-network ("bridgeness")
  - find k nodes with the greatest structural diversity (why?

## Querying Geo-Social Groups

- Zhu et al. arxiv’14: single query, find a dense group that is also spatially close
- Li et al. ICDE 2016: query node set, above + minimum group size 
- Y. Fang, et al, PVLDB’17: smallest minimum covering circle




