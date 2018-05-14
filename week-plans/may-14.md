core max

- [ ] check the cache update rule
  - refer to https://gitlab.com/xiaohan2012/daily-reading/blob/master/apr/non-adjacency-dependency-example.pdf

active cascade reconstruction

- try IC model
  - [ ] on grqc-sto
  - on infectious-sto
  - on nethept-sto
- query method comparison observing whether leaves or nodes close to root?
  - [X] root sampling procedure for close-to-root and leaves
  - [ ] run experiment
- manual checking query process on small graphs (karate club, dolphin , etc)
- [X] other evaluation metric other than p@k that does not give favor random?
  - number of nodes (including queried nodes) with p>0.5 that are actual infections
- experiment with the weighted conditional entropy strategy

- try more graphs (maybe euclidean graph)

- how good is the inference algorithm? how does the heatmap look like?
- what's the optimal query strategy given the ground truth (oracle)?
