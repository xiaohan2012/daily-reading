- read about graph inference problems (what I read in KDD 2017)

- [X] find other graph inference problems in kdd papers

- electrical network and random walk
  - chapter 1

- [X] think about random steiner tree and personalized random walk
  - is not very easy

- extreme multi-label learning: faster prediction. can I borrow the idea from sparse local embedding paper (clustering?)

- can we use the techniques in gradient boosted tree in fastxml? 

- wrap edmonds' algorithm
  - [X] usable by rejected paper

- experiment for rejected paper
  - refer to previous experiment's measurements 
    - prove that closure and delay-bfs is better
  - how come synthetic networks and real datasets give different result for the methods
  - [X] plug in the new edmonds' algorithm
  - experiment on more syntheitc graphs and real graphs
    - 4k nodes: http://snap.stanford.edu/data/egonets-Facebook.html
    - 1k: http://snap.stanford.edu/data/email-Eu-core.html
    - 5k: http://snap.stanford.edu/data/ca-GrQc.html
  - [X] separate the code
  - my own graph library


- active learning experiment
  - [X] ranking based evaluation
  - [X] inference method comparison using new evaluation
  - [X] better query process visualization
  - [X] query comparison
  - [X] interprete query comparison result

- network embedding
  - [X] use pre-trained node embedding
  - [X] use nce parameters as well
  - [X] preprocess more datasets
  - experiment on the datasets for three methods
    - [X] split train, dev and test data (80%, 10%, 10%)
    - [X] save running information to separate directory
    - [X] evaluation for each dataset
  - [X] presentation slides