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

