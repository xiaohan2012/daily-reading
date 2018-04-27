# prediction



# label partitioning

## representation

- label representation: mean of x whose y contains l
- label similartiy: dot product

alternatives

- [Label Embedding Trees for Large Multi-Class Tasks, NIPS 2016](https://papers.nips.cc/paper/4027-label-embedding-trees-for-large-multi-class-tasks.pdf)
  - uses graph cut, spectral method
- not considering label co-occurrence information: can use the co-occurrence vector as the feature as well. and use hashing to speed up
  - however, two frequently co-occuring labels should have similar vectors? 
  - so co-occuring implies similar vectors, is it true the other way around? I don't know

## partitioning

- k-means, with balanced (*strictly* half and half, I would say this is too strict)
- iterative/alternating optimization

## training

- each node/leaf trains `k` 1-vs-all linear separators given `k` children.


## prediction

- at each internal node, the learned linear separators decides to left or right or both.
- beam search is used to reduce the computation time


# questions

- are training points partitioned by the label partitions?