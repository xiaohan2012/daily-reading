# plan

## acitve learning

experiment "big picture"

- [ ] experiment: varying sampling method (fixed query methoad) (1.5h)
- [ ] experiment: varying query method (fix sampling method) (1h)

## core maximization

coding:

- [ ] exhausive search algorithm Cython (1.5h)
- [ ] comparison between the two in terms of objective on small graph(1h)
- [ ] plot the result and gain intuition (1h)


more

- [ ] inapproximability
- [ ] the problem version with one given node


## graph embedding presentation

- what to present: what I've read, categorize them and present their similarities and differences
- [ ] summarize https://arxiv.org/pdf/1706.02216.pdf (2h)


# Wednesday

- [X] frog: try to prove hardness of one node version (1h)
- [X] supermodularity of one node version (1h)
- [X] cikm (0.5h)
- [X] cut algorithm in Boost and Cython (3h)



## frog

some thinking on fixing the hardness proof of the core max problem. 

using the example I sent to Lorenzo. as `x` receives too many higher order edges. one way to fix is to avoid compansating edge for it. 

however, if `x` is connected to some node in the big clique (`n+1` nodes), then selecting the set will not promote `x`.

it's a dilemma. 

# Thursday

- [ ] frog: wrapper for steiner tree sample pool and refactoring (1+1h)
  - think: 1, what are the functions to implement, (`update_samples` for node removal and addition case), 2, what are the test cases
  - in Cython
- [ ] summarize https://arxiv.org/pdf/1709.05584.pdf (1h)
  - deeper model for node embedding
- [ ] read https://arxiv.org/pdf/1708.04828.pdf (0.5h)
- [ ] [is this algorithm optimal? try to come up with counter-example](december/subcore-algorithm.md) (1h)
- [ ] non-incremental greedy algorithm in Python/Cython (1h)