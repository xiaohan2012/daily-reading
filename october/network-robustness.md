# Graph measures and network robustness

# classifical measures

## distance

1. diameter
2. avg node pair distance
3. efficiency

all do not consider back-up edges (parallel edges)

after adding a edge (not parallel), the diameter can remain the same. 
however, distance and efficiency decrease. 

efficiency also works for disconnected graphs. 


## betweeness

sum of vertex/edge betweeness

inuition: vertex betweeness can identify the bottleneck of the graph. the higher the between, the more critical it is. 

therefore, the lower the value, the more robust

proved to be a linear function of avg distance. therefore, the three are essentially the same. 

## clustering

node clustering co-effcient: number of triangles containing $`i`$ / (deg - 1) deg * 2

clustering co-effcient of graph: average node clustering co-efficient

## reliability plolynomial

probability that the graph is connected after randomly removing edges with probability $`p`$

# spectral measures

## second smallest eigen value

- if graph is disconnected, it's zero
- it's a lower bound of the uniform sparsest cut

## number of spanning trees
 

## effective resistance

sum of effective resistance on each edge. 
  - ER on edge `(s, t)` equals to proba to start from `s` and visit `t` for the *first* time using edge `(s, t)`
  - strange definition

also equal to $`n \sum\limits_{i=2}{n} \frac{1}{\lambda_i}`$.

the smaller the more robust. 