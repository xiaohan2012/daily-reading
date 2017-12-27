# plan

## acitve learning

experiment "big picture"

- [ ] experiment: varying sampling method (fixed query methoad) (1.5h)
- [ ] experiment: varying query method (fix sampling method) (1h)


## core maximization

coding:

- [ ] non-incremental greedy algorithm in Python/Cython (1h)
- [ ] exhausive search algorithm Cython (1.5h)
- [ ] comparison between the two in terms of objective on small graph(1h)
- [ ] plot the result and gain intuition (1h)


- [ ] try to prove hardness of one node version (1h)
- [ ] [is this algorithm optimal? try to come up with counter-example](december/subcore-algorithm.md) (1h)

more

- [ ] inapproximability
- [ ] the problem version with one given node


## graph embedding presentation

- what to present: what I've read, categorize them and present their similarities and differences
- [ ] summarize https://arxiv.org/pdf/1706.02216.pdf (2h)


# Wednesday

- frog: [X] try to prove hardness of one node version (1h)
- [X] supermodularity of one node version (1h)
- [X] cikm (0.5h)
- [X] cut algorithm in Boost and Cython (3h)
- [ ] summarize https://arxiv.org/pdf/1709.05584.pdf (1h)
  - read summary/comparison of different methods
- [ ] wrapper for steiner tree sample pool and refactoring (1+1h)

## frog

some thinking on fixing the hardness proof of the core max problem. 

using the example I sent to Lorenzo. as `x` receives too many higher order edges. one way to fix is to avoid compansating edge for it. 

however, if `x` is connected to some node in the big clique (`n+1` nodes), then selecting the set will not promote `x`.

it's a dilemma. 

