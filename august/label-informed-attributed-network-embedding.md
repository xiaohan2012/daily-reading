# overview

- input: graph $`G`$ with node attribute matrix $`A`$, node label matrix $`Y`$
- output: embedding on nodes with labels, $`f: V \times Y \rightarrow H`$

three sets of embeddings:

1. structural $`U^{(G)}`$
2. attributed $`U^{(A)}`$
3. label $`U^{(Y)}`$

all three sets are combined into a joint embedding space $`H`$

# under construction

1. how to leverage label information in attributed network?

label information: sparse, noisy and incomplete (just right for stackoverflow)

attribute affinity matrix constructed by cosine similarity: $`S^{(A)}`$

- should be dense

why the maximization problem?

incorporate $`U^{(A)}`$ into $`U^{(G)}`$ by linear projection

