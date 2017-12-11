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
- [ ] meeting with Bapsite (1h)
- [X] meeting with Francesco and Lorenzo (1h)


## note

- [X] remove lemma 1 in document
- [ ] pseudo code: reflect using the edge score cache
- [ ] get candidate should track which candidate are returned
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