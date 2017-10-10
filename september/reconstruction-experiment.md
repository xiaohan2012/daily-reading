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

```
   74       119         1114      9.4      0.0          cpbfs_search(g, source=root, visitor=vis, terminals=list(late_terminals),
   75       119         7240     60.8      0.0                       forbidden_nodes=list(set(terminals) - set(late_terminals)),
   76       119     53260540 447567.6     97.8                       count_threshold=k)
```

```
Line #      Hits         Time  Per Hit   % Time  Line Contents
==============================================================
    59                                               @profile
    60                                               def black_target(self, e):
    61   2914677      7232975      2.5     70.1          t = int(e.target())
    62   2914676      2879264      1.0     27.9          if self.pred[t] == -1:
    63     51554        94979      1.8      0.9              s = int(e.source())
    64     51554        41574      0.8      0.4              self.pred[t] = s
    65     51554        64489      1.3      0.6              self.dist[t] = self.dist[s] + 1

Total time: 6.08986 s
File: /home/cloud-user/code/source_finding/utils.py
Function: tree_edge at line 67

Line #      Hits         Time  Per Hit   % Time  Line Contents
==============================================================
    67                                               @profile
    68                                               def tree_edge(self, e):
    69    959605      1855004      1.9     30.5          s, t = e.source(), e.target()
    70    959605      2064484      2.2     33.9          s, t = int(s), int(t)
    71    959605       928588      1.0     15.2          self.pred[t] = s
    72    959605      1241789      1.3     20.4          self.dist[t] = self.dist[s] + 1
```

it turns out I am wrong: `tree_edge` and `black_target` part only takes 20% of the time of `cpbfs_search`

so `cpbfs_search` itself is slow. 

# code structure

- `steiner_tree_order` contains code for `tfbfs` (name is confusing)
- `steiner_tree_mst` constains code for transitive closure approach

together put them in `core.py`


`GraphView(Graph(diredcted=False), directed=True)` does not add bi-directional edges. 


recap: when building the closure, we do constrained bfs that avoids late terminals

# different method comparison

## node precision/recall

- precision:
  - for ct, one dataset gives higher precision than other two 
  - for si, close to 1
- recall: expected for both ct and si

## edge precision and recall

- ct gives expected result (closure is better than bfs in precision but not on recall)
- while si does not

## order correlation

baseline is quite competitive, not sure if this is the correct way to evaluate. 

## order accuracy

- si favors delay-bfs
- ct favors closure


## what to show

across all datasets

- node precision and recall
  - for si

- edge precision and recall
  - for ct

- order accuracy
  - for ct



# real cascades: flixter

- flixter dataset by polina
- https://github.com/polinapolina/reconstructing-an-epidemic-over-time/blob/master/Data/flixter_1000_K9.txt
- too small

# real cascade: twitter

http://lsir.epfl.ch/research/datasets/socialnetwork/

```
@InProceedings{galuba-wosn10,
     author = {Galuba, Wojciech and Aberer, Karl and Chakraborty, Dipanjan and Despotovic, Zoran and Kellerer, Wolfgang},
     booktitle = {3rd {W}orkshop on {O}nline {S}ocial {N}etworks ({WOSN}'10)},
     title = {{O}uttweeting the {T}witterers - {P}redicting {I}nformation {C}ascades in {M}icroblogs},
     year = 2010
} 
```


# real cascade: digg

https://www.isi.edu/~lerman/downloads/digg2009.html from [this paper](https://arxiv.org/pdf/1202.3162.pdf)

only 50% edges are mutual friends. 

- graph is directed
- cascade does not form a connected component

simplification (might be invalid):

- extract only the largest cascade subgraph: 16531 nodes, 87452 edges
- extract only the largest cc in the cascade subgraph: the cascade contains 3741 nodes
- assume the graph is *undirected*

# sp and ic

pause: no-order, 0.065 done


# pandas

- `get_group(key)` from `GroupBy` object

# all models on one dataset

- node precision
  - grqc: desirable
  - email-eu: ic strange

- node recall: 
  - email-eu good
  - grqc: strange
  - ic flactuates

- order accuracy: email-eu gives relatively consistent result, but grqc does not
- edge precision:
  - email-eu nor grqc is consistent
  - ic flactuates
- edge recall
  - both grqc and email-eu favors tbfs (expected)
  - ic flactuates  

good news:

1. si and ct are favorable

bad news:

1. edge precision is low on certain graphs
2. ic and sp model favors tbfs on edge precision



# one model on all datasets

## ct

- order accuracy: good
- edge precision: closure good
- edge recall: tbfs good , expected


## si

similar as ct

good news: some model is good on all four datasets

# matplotlib

# limiting the number of ticks

https://stackoverflow.com/questions/13052844/matplotlib-how-to-decrease-density-of-tick-labels-in-subplots/13053381

# positioning text using figure transform

https://stackoverflow.com/questions/42435446/how-to-put-text-outside-python-plots



