# plan

## core maximization


- [ ] visualize the result (added edge, red)
- [ ] exhausive search (2h)
- [ ] experiment on grqc graph
- [ ] present result to Lorenzo and Francesco (1h)


## active learning

thinking:

- [ ] Is closure based sampling equivalent to wilson's version

coding:

- [ ] implement wilson's algorithm on steiner tree
- [ ] integrate it into `graph_tool`
- [ ] sample pool class that handles sample generation, update, etc
- [ ] speed comparison (with/without incremental update)

reading:

- [ ] time analysis of wilson algorithm
- [ ] non-uniform random spanning tree (understand the proof)


# Sunday

- frog: [X] think about the nc id that should be attached (1h)


# Monday

- [X] frog: unrooted version of wilson algorithm (1h)
- [ ] make the test pass (3 h)
- [ ] python interface and try on karate graph (1h)
- [X] cikm (0.5h)
- [X] meeting with Bapsite (1h)
- [X] meeting with Francesco and Lorenzo (1h)


## note

- [X] remove lemma 1 in document
- [ ] pseudo code: reflect using the edge score cache
- [X] get candidate should track which candidate are returned
- [ ] update the document

ended up with more tests to pass

## discussion

- [ ] study inapproximability of np-hard problem

# Tuesday

- problem formulation
- np-hardness, sub/super modularity (proof in appendix)
- greedy algorithm
- pruning strategy
- incremental update

## np-hardness proof mistakes

- [ ] a node's core might increase if we don't constrain the edges being added

solution: we don't have to compansate edges for nodes that are already compansated. 

- [ ] make sure that selecting sets do not mistakenly include extra elements. 

# Wednesday

- [X] polished document
- [X] thinking `update_subcore` and `update_bucket`
  - [doc](december/core-max-incremental-update.md)


what to do next:

- [ ] use Python for greedy algorithm and wrap the core update functionality since it should be the bottleneck.
  - maybe check how Cython is used

## discussion with Cigdem

to do during Christmas

- [ ] transitive closure documentation
- [ ] random spanning tree using coupling from the past paper (Section 6 and 7)
- [ ] code the loop erased random walk and transitive closure
- experiment: 
  - [ ] comparison of different sampling approach, do they accord well with the desired distribution?
  - [ ] active learning on larger graphs
  - [ ] effect of sampling approach on sampling methods

## dicussion with Lorenzo

- [ ] fix hardness proof, using the frequency bounded version of set cover
  - http://www.aaai.org/ocs/index.php/AAAI/AAAI15/paper/download/9674/9513
  - `f \le max|S|`, where f is the frequency
- when compansating edges, consider node-wise and use degree (c_{max}+2)or core to upperbound the number of edges. 

## discussion with Francesco

- [ ] disucss with Aris and ask if he wants to join. 
- [ ] weak point: greedy is too simple

possible directions:

- pruning for edge batches?
- figure of example of greedy's bad performance
- how many edges are requried to increase the core of a subgraph?



