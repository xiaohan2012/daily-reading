# multi-layer networks

# key concepts

- multilayer network, consists of 
  - a set of nodes
  - one or more sets of layers
    - each set represents a *dimension* or *aspect*
    - for example, one set is time, the other is edge type)
- elementary layer: one element in one set
- layer: combination of elementary layers from each set
- node layer tuple: a node with layer information

## constraints

- node-aligned: all nodes are in all layers
- layer-disjoint: nodes in each layer are disjoint with each other
- diagonal coupling: all inter-layer edges are between nodes in one layer and their counterparts in another layer
- (inter)-layer coupling: for any two layers, the coupling edges (and weight) are the same (except for the layers)
- categorical coupling: each node in one layer is connected to all its counterparts in other layers (
  - why this name? in contrast to ordinal coupling such as time aspect

# representation

- tensor: `{0, 1}^{|V| x |V| x |L_1| x |L_1| x ... x |L_d| x |L_d|}`
  - assumes the graph is node-aligned, might need to padd with empty nodes
  - may cause problem for network diagnostics
  - flattening: can be flattened for example for diaganol coupled graphs  
- supra-adjacency matrix: use node layer `V_m` as the nodes and `E_m` as the edges
  - pros: no need to add padding
  - cons: may lose some information
  - supra-laplacian can be defined similarly
    - algebraic connectivity
    - dynamic process
- node-colored networks
  - `G=(V, E, C, \chi))`, each node has a color/type from `C` defined by `\chi`
  - usually, layer-disjoint
  - in this framework: `d=1`, `L=C`, each color corresponds to a layer
- edge-colored/multiplex/multirelational networks
  - `G_{\alpha}` indexed by `\alpha`, which is one edge type
  - or `(V, E, C)` where `C` is edge type mapping function
  - does not require node-aligned


# questions

- how to represent Quora question graph in this framework (author, question, answer, user-vote, user-answer, user-reply)?
- how to represent Github repository graph (repository, user, issue, commit, user-star, user-watch, user-follow)

They are node-typed networks. 

# statistics for multilayer networks

- degree
- connectec components, to be continued


# further reading

- 138, 139 visualization of multilayer networks
- [56,118,119,126,129], [49,50], [57], [65,115], [151–153]

