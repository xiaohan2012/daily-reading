# plan

**core maximization**

- [ ] can we integrate our motivation with link prediction problems (according to topics, etc)? the objective contains both the recommendation score and core number

3h

**active learning**

- [ ] experiment: SDM2018 under different query strategies on grqc (0.5h)
- [ ] summarize the comparison between cut and loop_erased (1h)


8.5h 

**SDM paper**

- [ ] upload to arxiv if no modification needed (0.5h)
- [ ] tweet on Twitter and Weibo about it if arxiv id done (0.5h)

1.5h

**presentation**

- [ ] representation learning on bipartite graphs (with partial feature information)

4h

**internship**

one algorithm on [leetcode](https://leetcode.com/problemset/all/) per-day

- using python
- related to data structure (number theory is not very interesting)

more sites:

- [interviewbit facebook](https://www.interviewbit.com/facebook-interview-questions/#questions)
- [career cup](https://careercup.com/page?pid=facebook-interview-questions)


**reading**

- [X] [Representation Learning of Knowledge Graphs with Entity Descriptions](https://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/download/12216/12004) (0.5h)
- [Words are Malleable: Computing  Semantic Shifts in Political and  Media Discourse](https://arxiv.org/abs/1711.05603) (0.5+0.5h)

# monday

- [X] read [matrix as factorization](https://arxiv.org/pdf/1710.02971.pdf) (1h)
- [X] review the email, theory on loop erased sampling, prepare to explain the plan for experiment (0.5h)
- [X] TA (1h)
- [X] check Lorenzo's hardness proof (1h)
- [X] see if it can be adapted to hardness proof of the single node version (1h)
- [X] summarize the meta-review (0.5h)
- [X] meeting: (1h)
  - explain the the email on empirical tree distribution to true distribution
  - discuss experiment design
  - next plan
  - [X] ask Aris if it would be fine about the internship time frame
  - [X] ask Aris 
    - what should be done for the review
    - do I go to San Diego for conference
- [X] one leet-code problem


## meeting

for kdd submission:

- two main sampling procedures 
  - think about the time version
- [ ] write down the query strategy part
- experiment (part 1 and 2)
- scalability (incremental update)

for SDM paper:

- [ ] the idea of model invariant should be stated more clearly (Polina’s paper)
- [ ] compare with NetFill under different cascade model
- [ ] experiment with small cascade


# Tursday

- [X] distribute the topics using 40 pages (0.5h)
- [X] slides making: move what's on the paper to google presentation, add notes on random walk based approach as matrix factorization (1.5h)
- [X] using bipartite graph as the data structure for faster statistic calculation (1h)
  - algorithm and time analysis (should be better than quadratic except indexing)
  - efficiently update (remove/and add trees)
- [X] search for real cascade data (1h)
- [ ] why the code never stops and consumes no CPU resources (1h)
  - `cascade/grqc-s0.2-o0.1/91.pkl` never ends
- [ ] `inference.py` with incremental support (1h)
- [X] [Representation Learning of Knowledge Graphs with Entity Descriptions](https://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/download/12216/12004) (0.5h)
- [X] skim 5 papers in [WWW2018](https://www2018.thewebconf.org/program/social-network-analysis/)
- [X] interview coding exercise (1h)


## incremental update

how to avoid re-counting tree

# Wednesday

- [X] finish slides making (1h)
  - some text on deepcas
- [X] simulate what to say during presentation (1h)
- [X] search papers on cascade embedding (0.5h)
  - [here](jan/cascade-embedding-papers.md)
- [X] select two real datasets (0.5h)
  - let's use [flickr](http://socialnetworks.mpi-sws.org/data-www2009.html) and digg
- [ ] process one dataset (1h)
- [X] add more texts on scalability (1h)
- [X] skim 5 papers in [WWW2018](https://www2018.thewebconf.org/program/social-network-analysis/) (0.5h)
- [X] meeting (1h)
- [X] coding exercise


## meeting


- [Towards identity anonymization on graphs](https://dl.acm.org/citation.cfm?id=1376629)
- what's the minimum number of edges to add to promote a single subcore
- upperbound on a set of edges
- optimal solution for karate club: 
  - two edges span different subcores

action points:

- identify subcore but do not limit us to the subcore (neighboring nodes, even lower core nodes, can be benefited as well). a bit different from the previous intuition
- try other graphs to gain more intuition
- prove inapproximability: L-reduction
  - approximation preserving reduction
  - basad on reduction but preserve the approximation

# Thursday

- frog: [ ] find out why `cascade/grqc-s0.2-o0.1/91.pkl` never ends? (0.5h)
- [X] statistic calculator using 2d matrix as internal data structure (1.5h)
  - compare the time difference
- [X] presentation (1.5h)
  - gather feedback
  - encourage discussion
- [X] re-read subcore algorithm, find our what's wrong about the lemma (0.5h)
- [X] fix the wrong part, formalize the algorithm to find the set of edges, simulate on examples (1h)
- [ ] write the query strategy part (0.5h)
- [ ] case study, check other related papers on case studies (0.5h)
  - like news site dataset: does reconstructed tree reflect the infection order

## why never ends

located the problem and had two observations:

1. `graph_tool.Graph.remove_edge` fails to remove certain edges
2. `isolate_nodes` gives "kernel dies"

## presentation

feedbacks: 

- generally, it's a good summarization
- Aris questioned about the general property of word2vec formulation
- Kiran mentioned that graphsage has a natural structure for distributed computing

## max core

what's next:

- how to attach a single node
- design the greedy algorithm
- coding


# Friday

- [X] frog: case study, check other related papers on case studies (1h)
  - like news site dataset: does reconstructed tree reflect the infection order
- [X] update the subcore algorithm, change the setting to given a candidate edge set, and invalidate any subcores (1h)
  - [here](jan/promoting-subcore.md)
- [X] add prediction error to `tree_stat` (1h)
- [X] integrate matrix method into query selection (1h)
- [X] speed comparison (0.5h)
  - 2x faster than original impl on `grqc`
- [X] record the deleted nodes, simulate the isolation process on the grqc graph, see what will happen (1h)
- [ ] run algorithm on digg data set (1h)

## frog

- investigate on a small cascade on Digg, 
  - visualize the true cascade (on the small subgraph), node color as infection time
  - visualize also the reconstructed cascade (using 50% of the samples), node color as infection time 
  - does the two visualization match each other?
  - some example visualziation: https://research.fb.com/wp-content/uploads/2016/11/information_evolution_in_social_networks.pdf

- started to run experiments on small cascade

# Sunday

- takes a long time to sample one tree
  - related to how root are sampled