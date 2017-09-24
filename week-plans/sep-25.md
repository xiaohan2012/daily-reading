- read about active learning in general
- read about graph inference problems (what I read in KDD 2017)
- find other graph inference problems in kdd papers

- extreme multi-label learning: faster prediction. can I borrow the idea from sparse local embedding paper

- wrap edmonds' algorithm
  - usable by rejected paper
- experiment for rejected paper
  - refer to previous experiment's measurements 
    - prove that closure and delay-bfs is better
  - how come synthetic networks and real datasets give different result for the methods
  - plug in the new edmonds' algorithm
  - experiment on more syntheitc graphs and real graphs
    - 4k nodes: http://snap.stanford.edu/data/egonets-Facebook.html
    - 1k: http://snap.stanford.edu/data/email-Eu-core.html
    - 5k: http://snap.stanford.edu/data/ca-GrQc.html
  - separate the code
  - my own graph library

- active learning experiment
  - [ ] ranking based evaluation
  - [ ] full comparison (graph, observation)
  - [ ] query comparison (interpretable)
