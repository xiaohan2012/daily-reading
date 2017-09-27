# sep 13

pagerank is better than ours. possible reason:

- sample size for uncertainty computation is not big enough
- query number is big enough

however, the uncertainty computation produces the following side-product:

- beliefs on the other nodes' infection status

can we use it somehow?

# sep 27

use mutual information for query node selection. 
idea borrowed from the sensor placement paper. 

the goal is maximimze uncertainty reduction on the rest of the nodes

$`H(X_{V-O} \mid O) - H(X_{V-O} \mid O, A)`$

according to definition of conditional entropy

$`H(X_{V-O} \mid O)=-\sum\limits_{X_{V-O}} p(X_{V-O}, O) \log p(X_{V-O} \mid O)`$

- however, what's the form of $`p(X_{V-O}, O)`$? it depends on the infection model? 
  - for **continous time independence cascade  model**, this is defined
- also, $`V-O`$ has combinatorial structure
  - how to generate the samples? using techiniques from the "back to source" paper
  



