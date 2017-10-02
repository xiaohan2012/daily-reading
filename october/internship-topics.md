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

