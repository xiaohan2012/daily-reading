# pure embedding based multi label classification

learn two sets of embeddings for 

- each label
- each document

such that for each document, its embedding is as close as its associated labels. 

the objective is to minimize:

$`\frac{1}{N} \sum_d \sum_{l \in L(d)} d(e_d, e_l) + \text{regularization}`$

$`e_d`$ is calculated from some deep learning model such as CNN. 

training is done by optimizing $`e_d`$ and $`e_l`$ alternately. 

$`e_l`$ can be initlized by some network embedding method. 

- the graph: two labels are connected if they occur in the same document
