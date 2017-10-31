# week plan

- [X] friendster paper (1 h)
- influence maximization: influence definition, problem definition and approximation method (2~3 h)
- [X] resilience measures (2 h)
- find and read related work: modify graph structure to increase graph robustness (1 h)
  - example: https://www.researchgate.net/publication/301313634_Optimizing_network_robustness_by_edge_rewiring_a_general_framework
- Network Creation Game (1 h)

- extreme multilabel classification (1 h)
  - what's the prediction time of  SIGIR paper? 
  - how does it reduce it?
- two more papers on compression/decompression (new)
- metric learning tutorial: https://arxiv.org/pdf/1306.6709.pdf (1 afternoon)

## goal

- problem formulation of the friendster problem

# Sunday

- read fastxml paper

next step:

- understand the compression-decompression techniques
  - commonality and difference
- understand the tree based methods
  - LPSR and MLRF


# monday

- [X] **frog**: think about how to sample cascade (1.5 h)
  - how to estimate `H(t_y \mid O)=\int p(t_y \mid O) d t_y`? using cascades?
  - what distribution should the cascades be drawn from?
  - same question for conditional entropy part
- [X] graph robustness measure: (1.5 h)
  - https://arxiv.org/pdf/1311.5064.pdf
- [X] read https://arxiv.org/pdf/1302.6109.pdf (1.5 h)
  - how social resilience is quantified
- meeting with Cigdem (2 h)

## frog and discussion

problem is how to estimate `p(t_y \mid O)` using simulated cascades

- be formal about the form with hidden variable `C`

discussion:

- Cigdem thinks sampling from cascade to estimate entropy is not straight forward
  - she is thinking about querying selection based on minimizing prediction error
  - reminds of the standard and non-standard approach to do active learning
- suggests two papers to check
- plus Aris' two papers

next steps:

- Kleinberg's paper
- effective resistance note
- four papers by Aris and Cigdem

# Tuesday

- [X] anchored k problem paper (1 h)
  - what's the problem formulation
- [X] frog: think about our formulation (2 h)
- [X] Toward optimal active learning through monte carlo estimation of error reduction: http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.137.6296 (1 h)
  - what's the objective to optimize here?
- [ ] Fabio's active learning paper (1 h)
  - what's the objective to optimize here?
- [ ] active learning for uncovering biological network: http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005466 (1 h)

# frog

formulated the problem, the objective has recursive form. 

what's unknown:

- is it NP-hard?
- submodularity on recursive function
  - https://arxiv.org/pdf/1701.08939.pdf: section 4.1

next:

- can we reduce the original problem as a special case to our problem?
- if not, can we us the NP-hardness proof in kleinberg's paper to our case?
- related problem: add edges to maximize some function on k-core (ego, or global)
  - what's the driving factor for network unraveling (friendster paper)

