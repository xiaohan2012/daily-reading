http://scikit-learn.org/stable/modules/clustering.html#clustering-evaluation

# supervised

- ARI: adjusted random index
  - [-1, 1]
  - 0 if random clustering
- NMI: normalized mutual info
  - not normalized against chance
  - [0, 1]
- AMI: adjusted mutual info:
  - normalized against chance: random clustering has 0 score
  - [0, 1]

- homogeneity: each cluster contains only members of a single class.
  - like precision
- completeness: all members of a given class are assigned to the same cluster.
  - like recall
- v-measure: harmonic mean of the above
  - like f1

- intuitive
- not normalized against chance

effect of cluster number on score against random clustering

![](http://scikit-learn.org/stable/_images/sphx_glr_plot_adjusted_for_chance_measures_0011.png)

- Fowlkes-Mallows scores


# unsupervised

- [Silhouette Coefficient](http://scikit-learn.org/stable/modules/clustering.html#silhouette-coefficient)
  - idea: a good clustering should satisfy 1) each cluster is dense 2) clusters are well-separated
  - requires vector representation for each node
  - requires distance measure
  - [-1, 1]
  - **question**: does the number of clusters play a role?
- [Calinski-Harabaz Index](http://scikit-learn.org/stable/modules/clustering.html#calinski-harabaz-index)
  - similar idea as Silhouette Coefficient
  - lower bounded by 0 and unbounded upwards
  - the larger the better
  
