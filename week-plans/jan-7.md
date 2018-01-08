# plan

**core maximization**

- [ ] can we integrate our motivation with link prediction problems (according to topics, etc)? the objective contains both the recommendation score and core number

3h

**active learning**

- [ ] learn how to run NetFill (1h)
- [ ] experiment: SDM2018 under different query strategies on grqc (0.5h)
- [ ] summarize the comparison between cut and loop_erased (1h)
- [ ] Python interface for NetFill (2h)


8.5h 

**SDM paper**

- [ ] upload to arxiv if no modificatio needed (0.5h)
- [ ] tweet on Twitter and Weibo about it if arxiv id done (0.5h)

1.5h

**presentation**

- [ ] some thinking on cascade embedding or network alignment
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

- [Representation Learning of Knowledge Graphs with Entity Descriptions](https://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/download/12216/12004) (0.5h)
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
- [ ] case study, check other related paper on case studies
  - like news site dataset: does reconstructed tree reflect the infection order?

# Tursday

- [ ] distribute the topics using 40 pages (0.5h)
- [ ] slides making: move what's on the paper to google presentation, add notes on random walk based approach as matrix factorization (1.5h)
- [ ] using bipartite graph as the data structure for faster statistic calculation (1h)
  - algorithm and time analysis (should be better than quadratic except indexing)
  - efficiently update (remove/and add trees)
- [ ] search for real cascade data (1h)
- [ ] why the code never stops and consumes no CPU resources (1h)
- [ ] `inference.py` with incremental support (1h)
- [ ] [Representation Learning of Knowledge Graphs with Entity Descriptions](https://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/download/12216/12004) (0.5h)
- [ ] skim 5 papers in [WWW2018](https://www2018.thewebconf.org/program/social-network-analysis/)
- [ ] interview coding exercise (1h)
