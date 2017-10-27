# Querying K-Truss Community in Large and Dynamic Graphs

- k-truss definition: each pair of nodes has east least $`k-2`$ common neighborss
  - so minimum of $`k`$ is 2. 

- original definition of k truss [7]
- truss decomposition [21]


# concepts

defs:

1. support of edge: num of triangles it's in in a given graph
2. adjacent triangles: two triangles are adj if they are one edge
3. triangle connectivity: two triangles are connected if there are a series of other trianlges that are adjacent to its neighbors. 
4. k-truss community: 
   1. k-truss
   2. edge connectivity: all triangles inside are connected
   3. maximum: does not exists its subgraph to satsify 1 and 2

condition 2 is used to ensure connectivenss and cohesiion

- connectiveness: the k-truss without 2 can be disconnected
- cohesion: the k-truss without 2 can be not coherent. so a query node can be in more than one k-truss communities. 
- see Figure 2

# properties of k-truss

1. bounded diameter
2. (k-1)-edge-connected: removing any $`(k-1)`$ edge still keeps it connected
3. polynomial time for k-truss decomposition: [7, 21]

1 and 2 are reltaed to criteria of a good community.

variants of k-truss community:

- denest: maximize k
- diverse communities: communities of similar sizes

# problem

given a query node $`v_q`$ and integer $`k`$, find all k-truss community that contains $`v_q`$

# querying

def:

- subgraph trussness $`\tau(H)`$: minimum of edge support in subgraph
- edge trussness $`\tau(e)`$: maximum support from all subgraphs, corresponding subgraph is $`H^e`$

in other words, if edge $`e`$ has trussness $`k`$, there must exist a connected subgraph $`G^{'}`$ that gives $`sup(e, G^{'}) \ge k`$. 

note that the subgraph is composed of triangles (except for $`k=2`$)

## truss decomposition

used as the initialization step. 

goal: compute trussness of all edges. 

algorithm: idea similar to core decomposition - "peeling"
  - order the edges by support
  - for the current edge, update its adjacent edges' support, set its $`\tau`$ value and remove it from $`G`$
    - requires ordering of the edges by updated support
  - repeat the process

analogy to core decomposition: 1, order nodes by degree, 2, update adjacent nodes' degree.

## simple index

the graph is stored in adjacency list format. 

- neighbors for each node are sorted by their truss value in descending order (because the values are integers, sorting can be done in linear time). 
- edge trussness values are stored in hashtable

- time complexity: $`O(\sum\limits_{(u, v)} \min\{d(u), d(v)\})`$
- space complexity: $`O(m)`$

## query processing

performs a variant of BFS. 

basic idea:

- traverse edges by triangle adjacency (edge is like node, adjacency is defined by triangle adjacency)
- we visit an edge only if its trussness $`\ge k`$

we do this $`BFS`$ for each adjacent edges of $`q`$. 

- time complexity: $`O(|Ans| d_{max})`$ (line 7, 8)
  - $`Ans = C_1 \cup \ldots \cup C_l`$

# TCP-index (Triangle Connectivity Preserved Index)


problem with simple index

- repeated access of qualified edges: each edge is visited $`2(k-2)`$ times. the total time lower bounded by $`\Omega(k|Ans|)`$
- unnecessary access of disqualified edges (line 9)

# comment

k-truss is very related to k-core. in k-truss:

- an edge is like a node
- edge support is like node degree. 
- edge adjacency is defined by triangle adjacency. 






