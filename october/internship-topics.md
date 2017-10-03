# matching dense attributed subgraph by query in sliding window

what's the application?

the subgraph changes overtime, we want to capture that. 

what kind of graphs have such change. 

collaboration graph: edges change, attributes change

# dense and label heterogenous subgraph detection by query 

application: a set of nodes might be involved in different communities. 

note that query does not include attributes

for example, two authors might be involved in multiple communities

a straightforward approach:  find the densest matching subgraph and split the subgraph into sub-subgraphs by labels. 


# papers

- http://www.vldb.org/pvldb/vol10/p949-huang.pdf
- http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.477.4053&rep=rep1&type=pdf
- FIRST, Fast Interactive Subgraph Matching
- Graph Query Reformulation with Diversity
- [diversified top-k graph pattern matching](https://dl.acm.org/citation.cfm?id=2536263)

# community search papers

- http://www.vldb.org/pvldb/vol10/p709-fang.pdf
- http://www.cs.hku.hk/research/techreps/document/TR-2016-01.pdf
- http://www.vldb.org/pvldb/vol10/p709-fang.pdf

## variants

- community search on multi-layer graphs
- community search in sliding window
- diversified top-k community search

# anchored k cores

- https://www.cs.cornell.edu/home/kleinber/icalp12-kcore.pdf

**variant**:  anchored k-core in uncertain graphs

# add edges to maximize weight average core size

add `b` edges so that

`\sum\limits_{k=2} \frac{|core(k)|}{|V|} \cdot k`

is maximized

or maximize inner-most core size, or maximize core of size `k`

applications:

1. link recommendation

# random thoughts

## explorative community search

## community search over node-typed network

queries: nodes of different types, 

- user/video/webpage
- author/paper/keyword
- person/account/address

definition of k-core in multi layer network


