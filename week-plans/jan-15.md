# plan

## NetFill experiment for KDD submission and SDM paper

- [ ] Python interface for NetFill (2h)

## SDM paper

- copy right form
- follow instructions


## KDD submission

goal: by next Friday.

- experiment comparing different query strategies
- experiment comparing different sampling strategies
- the algorithm/implementation is optimized

## core maximization

goal: some algorithm inspires from the optimal solution on karate club (based on subcore algorithm)

- [ ] state the difference between version with given candidate set of edges and with the complementary edge set 
- [ ] subcore algorithm: after matching as many nodes, what to do with the rest unmatched nodes? how to maximize the gain?
- [ ] greedy algorithm
- [ ] experiment on graphs with reasonable size
- [ ] matching based core update paper


# monday

- [X] ML coffee talk (1h)
- [X] frog: profile code for entropy method (1h)
  - what's the bottle neck, optimize it? (?h)
- [X] review optimizing scalability using lazy evaluation (0.5 h)
- [X] is it appliable to entropy/prediction error method (0.5 h)
- [X] if applicable, state it in the document (0.5h)
- [X] meeting (1h)
  - current progress
  - scalability issue
- [X] extract the subgraph of the karate club and investigate what's the case of the optimal solution for greedy (1h)
  - could subcore algorithm be applied to this case?


## profiling entropy method

- unstable:  the tree sampling can take a long time, can we just set time out for early stopping
  - what's the reason for this?

the main bottle neck is sampling a steiner tree

**incremental tree sampling** 

instead of sampling a tree from scratch, we can sample a new tree based on previously sampled trees (the trees might not be valid for the current observation)

for example, 

- if the queried node is infected, we can attach this node to the current tree (assuming the tree does not contain it)
- if the queried node is uninfected, we just moreve this node from the current tree (assuming the tree contains it)

**observation**

the first node takes a longer time connect and it also gives larger standard deviation

## meeting summary

- [X] pure version with no approximation
- [X] experiment on smaller graphs

## optimal solution structure

- core-3 node connects to 3 nodes in core-4
- core-4 has two nodes with degree < 5
- two edges give the boost, even though there is not inter-core edges


# tuesday

- [X] check the problem for the peer (0.5h)
- [X] mock-up (1.5h)
- [X] time-profiling the pure version (1h)
- [X] unify the inconsistent sampling problems (0.5h)
- [X] document promote-node: which has `\deg^{+} == K` and core number smaller than (0.5h)
- [ ] write algorithm:
  - calculate minimum number of edges required to promote a subcore (1h)
  - subcore which returns the subcore (1h)
- [ ] case study on small datasets (1h)
  - graph topology visualization
  - node states viz

## interview

fail to solve the problem (implementing LRU cache), lessons learned:

- good to write my idea on the codepad
- need to improve my communication skills (speak slowly for example)
- basic data structures are usually built-in (no need to implement by myself)
- use linked list for fast insertion and removal
- hashtable lookup for fast access of linked list element

## subcore algorithm

- switched to the candidate-edges version
- not easy to determine the number edges required to promote the subcore (needs to run the maximial matching algorithm)
- `promote-node` can be done by `best-edge`

some new idea:

following the optimal solution on karate club, we can operate on the subcore `sc` plus intermediate lower-core neighbors `N(sc)` that connect to the subcore (with edges only connecting between `sc` an `N(sc)`). 

then we define the following problem: 

we want to add the minimum number of edges so that:

1. all nodes in subcore get promoted to the next core
2. the number of nodes in `N(sc)` that get promoted is maximized

a bit weird: a min-max problem

essentially a matching problem, each node needs to be matched `c(v)+1-\deg^{>=}(v)` times. 
For nodes in sc, it need to be matched at most once. 
For nodes in `N(sc)`, it need more than 1 matched edges. 

blossom algorithm:

- https://en.wikipedia.org/wiki/Blossom_algorithm
- https://www.cs.dartmouth.edu/~ac/Teach/CS105-Winter05/Notes/kavathekar-scribe.pdf


# Wednesday

- [X] frog: prepare for the subcore/matching problem (1.5h)
  - motivation: plot the complementary graph, show what subcore/matching algorithm gives (0.5h)
  - state the matching problem formally (0.5h)
  - write down the bullet points for meeting (0.5h)
- [X] is the score decreasing as iteration number? (0.5h)
  - if necessary, plot the trend
- [ ] if so, integrate the lazy evaluation strategy (1h)
- [ ] run the experiment on one smaller graph (grqc if it does not take too much time) (0.5h)
- [X] learn how to run NetFill (1h)
- [X] meeting: Barbbar (0.5h)
- [X] plot for small cascade and writing (0.5h)
- [X] meeting: Francesco (1h)

## meeting prep

part 1:

- optimal vs greedy on karate (Figure 5)
- Figure 6: K=4, goal: make it 5
  - a:
    - why degree from inner most core: edges from them are *always* valid to promote
  - b: 
- can we gain any intuition from this example?

part 2: subcore

- main question: how to promote one subcore (without considering external nodes)
  - using the Figure 6 as the motivation (ideally, we just add two edges to match two nodes)
  - Figure 4: (complementary graph on pink nodes)
    - only need to operate on the pink nodes

## lazy evaluation

- inapplicable for `argmin prederror(query)`
- wondering why not `argmax`

## notes on NetFill

- `ssh tal`
- `ssh triton`

in `DEMO.m`:

- `G`: adjacency list

- `D`: true infection state vector
- `SD`: observed state vector
- `p`: the `q` parameter in our case
- `C_netfill`: predicted infection states???
- `S_netfill`: predicted seeds???

## discussion with Rohit

number of points per label indicates the performance of different methods:

- the larger the number, the more likely for labels to co-occur, therefore better for methods that model label correlation
- however, the sparser the label graph, the better one-vs-rest works

- can we combine the good parts on both one-vs-all and embedding based method?

## meeting with Francesco and Lorenzo

- bin matching (each node has a capacity to match)
  - bipartite matching: modified from max flow algorithm (using source and sink node)
- [ ] lorenzo's idea on identifying the influential node and try to match them 
  - "influential node v" by the number of nodes that will get promoted if `v` is promoted
- [ ] compare greedy, subcore and Lorenzo's algorithm on larger graphs

## mockup

lessons

- talk more so to think
- write the basic skeleton/signature first and fill in the details

# Thursday

- frog: [X] infection probability with incremental support and using tree_stat (1h)
- [X] query experiment using random and pagerank
- [X] probability inference on `loop_erased` and all query methods
- [X] experiment using cut algorithm on grqc (entropy, prediction error min, max)
- [ ] plot result on grqc (random, pagerank, entropy, prederror-min, prederror-max) (0.5h)
- [X] plot evaluation excluding the observation (0.5h)
  - [X] update figure (0.5h)
- [X] understand blossom algorithm for matching (1h)
  - [c++ code](http://codeforces.com/blog/entry/49402)
  - didn't understand yer. covered augmenting path and def of blossom
- [X] the bin matching idea: search papers, instead of capacity, use demand (relation to flow problem with min requirement?)
- [ ] why one-vs-rest performs well? how to improve its prediction accuracy?
  - DiSMEC - Distributed Sparse Machines for Extreme Multi-label Classification

## papers on matching with demand

- max flow with node demand: http://courses.cs.vt.edu/cs5114/spring2013/lectures/lecture19-network-flow-applications.pdf
- max flow with edge demand: https://web.engr.illinois.edu/~jeffe/teaching/algorithms/2009/notes/18-maxflowext.pdf
- https://cs.uwaterloo.ca/research/tr/2006/CS-2006-33.pdf

## sdm paper


- found that facebook on si model, recall is very strange

# Friday

- frog: [X] integrate  sdm method in inference  
- [X] run inference on on `{cut, loop_erased}` x `{inf_probas, order-steiner-tree}` on grqc
  - curious to see if `prediction_error-max` works
- [ ] plot result on grqc `{loop_erased, cut}` x `{inf_probas, order-steiner-tree}`(0.5h)
  - 4 plots
- [X] why recall of si+facebook is strange? fix it (0.5h)
  - to run `./scripts/gen_eval_cmd.sh`
- [X] check Cigdem's email (0.5h)
- [X] update the problem formulation
- [X] writing for query strategy part (1h)
- [ ] formalize the order respecting version using loop_erased random walk (0.5h)
- [X] follow instructions of the camera ready version, list what to do (1h)
- [X] print flight ticket


## bug when running greedy

> processing cascade/grqc/95.pkl started, query_method=pagerank, inference_method=order_steiner_tree


## SDM

- January 24, 2018, by 11:59 PM PT:  final version
  - 9 pages max
  - abstract maximum of 300 words
  - max 6 keywords
  - agree the copyright transfer form  
- January 26: travel grant application
- Feb 5: Submit presentation information
- April 3: preregister

todo: 

- [ ] small cascade experiment, re-run, eval, plot, update figure
- [ ] large cascade experiment, re-run, eval, plot, update figure
- [ ] fix x-axis for large cascade
- [ ] update text in experiment