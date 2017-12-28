# Multi-Task Neural Network for Non-discrete Attribute Prediction in Knowledge Graphs

main goal: representation learning using *non-discrete attributes* (height, weight, etc) under *multi-task* supervision. 

some notions:

- triplet: (head, relation, tail)
- relational learning, examples:
  - infer probabilities of new/unseen triplets. 
  - completion, example: `(person, hasGender, ?)`

# model 

## input

a set of entities `E` and a set of relations and `R`

`E \times R \times E` forms triplet space

## parameters to learn

embedding for both `E` and `R` 

- for relation, it might be a matrix, instead of vector

## probability functions

given a triplet, we can have its probability of being true.


**Entity Relation Multi-Layered Perceptron**

- concat `e_i`, `e_j` and `r_k`
- linear projection using `W`
- activate

quite strong in practice (YAGO and Freebase)

**Neural Tensor Network (NTN)**

- `e_i W_k e_j` to model the interaction


## objective function

examples:

- hinge loss
- cross entropy

# evaluation methods

- AUC
- accuracy (threshold set by dev set)
- attribute value prediction (numerical)