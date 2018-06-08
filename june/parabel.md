
# parabel

# basic idea

- train by partitioning labels (`Y`) not features (`X`)
- each internal node has two classifiers (one for going left or not and the other for going right or not, they operate independently)
- 

## label similarity

- label representation: mean of feature vector of associated training instances
- similarity: dot product


# questions

## label graph using vector similaity or co-occurence information: are they similar to each other

an example where they give different edges

consider two labels, l_1 and l_2, `l_1` has instances `X_1, \ldots, X_k` where `l_2` has instances `X_{k+1}, \ldots, X_{N}`, 
in other words `l_1` and `l_2` do not share any training instances, therefore for co-occurence graph, no edge is between `l_1` and `l_2`.

if `X_1, \ldots, X_N` share many similar terms, then using vector similarity, `l_1` and `l_2` have a large-weight edge.

In summary, similarity approach gives a superset of edges compared to co-occurrence graph. Two labels co-occurring together have high sim value, while two labels with sim value does not necessarily co-occur together

which is better? 

well, in experiment, they show the similarity based approach is better.

## what's the computational bottle-neck?

  - classifier?
  - k-means partitioning?

## about prediction in the code

don't quite understand how the prediction is done


# why use metis? my assumption:

- it's faster than k-means? what are the compleity of each method?
- it gives better partitioning? w.r.t stability and quality

time complexity of metis

- a graph in general: `O(n+m+k\log(k))` [ref](http://glaros.dtc.umn.edu/gkhome/node/419), 
- for sparse graph and `k=2`, it's `O(n)`
- for parabel (sparse label graph): `O(n \log n)`
  - preprocessing time to build knn graph (use kd-tree): `O(n \log n)`

