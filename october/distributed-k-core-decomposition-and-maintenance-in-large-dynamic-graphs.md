# Distributed k–core Decomposition and Maintenance in Large Dynamic Graphs

# overview

- nodes are partitions into disjoint set into each cluster node
  - edges that cut across different partitions are called *frontier edge*
- whenever an edge $(u, v)$ update arrives, master ask the workers to find the set of nodes whose core number should be updated (**M2W** mode)
  - a distributed DFS is done to find the updated nodes
- once such nodes are found, return them to the master to update

initialization:

- partition the nodes and compute the k-core in each parition locally
- for the frontier edges, consider them as edge insertion

# what can be improved

- use other maintenance scheme (like order-based approach) because it relies on VLDB paper's result on the set of candidate nodes
  - it's not clear how the set of candidates are updated (because some *maybe* updated)
- node partition scheme: it's like balanced min-cut partition
  - does this minimize the communication cost?
  - what if we group them by core-number as only the nodes with same core number are updated
- it considers sequential edge insertion still	 
  - batch insertion?

# learned

- one way to split the node
- one way to do the distributed core update: master-slave framework
  - different communication models: M2W, W2W, local


# what to learn next

- edge removal case
