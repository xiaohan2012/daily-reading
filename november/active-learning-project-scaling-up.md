# active learning project: scaling up 

# bottleneck

## stats

- `q2score = {q: score(q) for q in tqdm(self._pool)}`: > 90%
- `p = len(matching_trees(sub_T, u, 0)) / len(sub_T)`: 76.2%
- in `matching_trees()`, `return [t for t in T if node not in t]`: 93%

## complexity

it takes `O(n^2)` to select one query. `O(n)` candidates and for each candidate get the prediction error takes `O(n)`

# approaches

two ways to approach: 

## estimating prediction error by sampling

for the prediction error calculation, 

sample a subset of nodes (reduce the second `n`) to 

the question is: which nodes to use as sample?

ideally, nodes that are (almost) sure to be infected/unfecinted shouldn't be used.

so nodes' infection probability that are closer to 0.5 should more likely to be selected. 


## pruning candidates

intuition:  if node is not in any infection tree (almost sure to be uninfected), it won't give any useful information

so we throw it. 

similarly, if a node is in every infection tree (almost sure to be infected), throw it

interesting question: 

prove these nodes have higher predicted error mathematically
