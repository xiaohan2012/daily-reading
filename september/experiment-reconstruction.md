# things to optimize

1. output result takes a lot of space
2. closure construction and edmonds' algorithm are the main bottleneck

# time consumption on `ordered-mst`

```
   105         1            4      4.0      0.0      gc, eweight, r2pred = closure_builder(g, root, terminals,
   106         1            2      2.0      0.0                                            infection_times,
   107         1            2      2.0      0.0                                            strictly_smaller=strictly_smaller,
   108         1            2      2.0      0.0                                            k=k,
   109         1            2      2.0      0.0                                            debug=debug,
   110         1    148820533 148820533.0     39.3                                            verbose=verbose)
   111
   112                                               # get the minimum spanning arborescence
   113                                               # graph_tool does not provide minimum_spanning_arborescence
   114         1            4      4.0      0.0      if verbose:
   115         1          755    755.0      0.0          print('getting mst')
   116         1      2611817 2611817.0      0.7      gx = gt2nx(gc, root, terminals, edge_attrs={'weight': eweight})
   117         1            4      4.0      0.0      try:
   118         1    225646884 225646884.0     59.6          nx_tree = nx.minimum_spanning_arborescence(gx, 'weight')
   119                                               except nx.exception.NetworkXException:
```

## `build_closure`

most time on 

```
   71      3205        26537      8.3      0.0          cpbfs_search(g, source=root, visitor=vis, terminals=list(late_terminals),
    72      3205       201234     62.8      0.0                       forbidden_nodes=list(set(terminals) - set(late_terminals)),
    73      3205   1243017283 387836.9     96.1                       count_threshold=k)
```

this is one bottle neck I believe

```
    65                                               def tree_edge(self, e):
    66  25247842     92221318      3.7     53.1          s, t = int(e.source()), int(e.target())
    67  25247842     28369457      1.1     16.3          self.pred[t] = s
    68  25247842     53176873      2.1     30.6          self.dist[t] = self.dist[s] + 1
```