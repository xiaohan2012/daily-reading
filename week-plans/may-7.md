# core max tasks

- [X] more graphs
- [X] random edges (MF creates a bias)
- [X] candidate = non-edges on small graphs
- [ ] optimal solution on solutions
- [ ] check the cache update rule
  - refer to https://gitlab.com/xiaohan2012/daily-reading/blob/master/apr/non-adjacency-dependency-example.pdf

- [ ] dense subgraphs: take the dense cores and add edges to the core
  - largest subgraphs such that add k edges and it become and clique


# Wednesday

- [X] more graphs and random edge generation in a grid of plots
- [X] randon walk convergence rate
- assignment 3 last question

what's the infection probability distribution for SI and cut?


# Friday

- to check
  - query process illustration on `grqc_sto`, does queries in `community` intuitively better than those in `si` model
  - query method comparison, is pagerank still the best in L2 (legend=query method)
  - performance comparison between SI and COM (legend=cascade model)
  - infection probability on com model (does infection probaility seperate in COM better than SI?)
- [X] query performance on nethept
  - need to rerun `run.sh` to do inference for missing entries
- assignment 3 last question
- [X] laplacian


Meeting summary:

- try IC model
- query method comparison observing whether leaves or nodes close to root?
- manual checking query process on small graphs (karate club, dolphin , etc)
- other evaluation metric other than p@k that does not give favor random?
  - number of nodes (including queried nodes) with p>0.5 that are actual infections
- experiment with the weighted conditional entropy strategy

- try more graphs (maybe euclidean graph)

- how good is the inference algorithm? how does the heatmap look like?
- what's the optimal query strategy given the ground truth (oracle)?