# Tuesday

- effect of roots on our method, can it beat pagerank?
  - [X] using true root: in some cases, it can beat pagerank
- [X] effect of resampling, does it improve the result?
  - re-sampling is hard because of the high variance

- [X] effect of num. samples
  - 5000 is totally sufficient
- [X] observing on leaves/bfs-head
  - fix cascade fraction, vary obs fraction
- more graphs




# thursday

- [X] effect of true root on the two new graphs
- [X] try real cascade
- more data sets (infrastructure graph, etc)
- understand netfill paper
  - [ ] why they min(q) is 0.5
  - [ ] experiment on real cascades
- [X] how netfill can copy with sparse matrix?
  - create the sparse matrix: `S = sparse(i,j,v)`, where `i` is row, `j` is col and `v` is value
  - run it: `complete(SD, beta, S, missing, p, bulk);`

## datasets by netfill

- memetracker: requires contructing network using NetInf
- flixster: sent an request for the dataset

# friday

- implement root selection method: centroid
- report result on min dist root selection

experiments to run

- netfill on models|datasets
   - [X] gen data
   - [X] running
   - [X] done
- netfill digg:
   - [X] running
   - [ ] done
- random root, pagerank root on digg:
   - [X] running
   - [ ] done
   - min-dist root is not scalable
- re-run on methods|models|graphs
  - [X] gen data
  - [X] running
  - [X] done
- root sampler: min-dist, pagerank on digg dataset
  - [X] running
  - [X] done
- min_dist/pagerank using weight
  - [X] running
  - [X] done
- edge recovery experiment
  - [X] gen cascade with edges
  - [X] infer edge probability
  - [X] build the pipeline
  - [X] our
  - [X] min steiner tree
  - [X] running
  - [ ] done
- root selection on all graphs:
  - [X] running
  - [X] done


## plot

[X] **root selection**

- each graph per plot
- legend: root selection strategy
  - pagerank
  - min_dist
  - true root
  - random

[X] **comparing with baseline (node recovery)**

- each graph per plot
- legend: baseline
  - our (min_dist)
  - pagerank
  - min steiner tree
  - netfill
  - our (true_root)

[ ] **comparing with baseline (edge recovery)**


[X] **real cascades**

node recovery MAP

- pagerank
- min-st-tree
- our