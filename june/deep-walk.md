# DeepWalk: Online Learning of Social Representations, KDD 2014

unsupervised method that learns node features based on graph structure, independent of the labels `Y`

input:

- graph
- `X`: node features
- `Y`: partial node labels (can be multi-label)

output:

- node embedding `X_e` independent of `Y`


# main idea

- use short random walks to associate with each node
  - analogy: a list of surrounding short sentences associated with each center word
- language modeling techniques (such as word2vec) can be used for this case


## benefits of "short/truncated" random walk

- local nature: easily parallelizable
- online computing: if graph structure changes, only recompute the affected random walks.

## benefits of using node to predict its surroundings

in language model, this design throws away the order information, which might be useful.

but in network, "nearness" is more important than order.

# learned

- adapting language modeling technique to graph embedding
  - core idea of LM: a word `w`'s surrounding words define `w`
  - similar idea: a node `v`'s surrounding nodes define `v`

# thinking

- can it be used for node-colored networks?
  - random walk might not be "random" should depend on edge types
- how does word2vec work? why it works?  