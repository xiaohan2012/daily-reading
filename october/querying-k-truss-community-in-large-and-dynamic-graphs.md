
- k-truss definition: each pair of nodes has east least `k` common neighborss

- original definition of k truss [7]
- truss decomposition [21]


- truss decomposition
- building index for querying
- dynamic graphs: how to efficiently update the index for newly inserted/deleted edge

defs:

1. support of edge: num of triangles it's in in a given graph
2. adjacent triangles: two triangles are adj if they are one edge
3. triangle connectivity: two triangles are connected if there are a series of other trianlges that are adjacent to its neighbors. 
4. k-truss community: 
   1. k-truss
   2. edge connectivity: all triangles in side are connected
   3. maximum: does not exists its subgraph to satsify 1 and 2

condition 2 is used to ensure connectivenss and cohesiion

- connectiveness: the k-truss without 2 can be disconnected
- cohesion: the k-truss without 2 can be not coherent. so a query node can be in more than one k-truss communities. 
- see Figure 2

# properties of k-truss

- bounded diameter
- (k-1)-edge-connected: removing any `(k-1)` edge still keeps it connected
- polynomial time: [7, 21]

variants of k-truss community:

- denest: maximize k
- diverse communities: communities of similar sizes


# querying

def:

- subgraph trussness `\tau(H)`: minimum of edge support in subgraph
- edge trussness `\tau(e)`: maximum support from all subgraphs, corresponding subgraph is `H^e`










