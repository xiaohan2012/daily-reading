# CANE: Context-Aware Network Embedding for Relation Modeling.

[paper](http://nlp.csai.tsinghua.edu.cn/~tcc/publications/acl2017_cane.pdf)

# motivation

*multiple* embedding vectors for each vertex, to capture various aspect/context of the vertex

embedding of a node depends on its neighbor

# summary

embedding = structural embedding `concat` text embedding

- text embedding is context-aware (taking into account of the edges)

# setting

- directed and weighted graph
- deals with network with text information (generalizes to other types of information as well)

# model

## embedding

- context-free embedding: embedding of a vertex won't change (w.r.t the vertex it interacts with)
- context-aware embedding: given an edge (u, v), embedding of `u` depends on `v` and vice versa

two types of embeddings per node:

- `v^s`: structure-based embedding
- `v^t`: text-based embedding
  - can be either context-free and context-aware
- concatenation of `v^s` and `v^t` gives the complete embedding

## objective

- structural embedding is parameter while text embedding is not (obtained from other model)
- summation of structural and text embedding
  - `sum_e L(e)`
  - `L(e) = L_s(e) + L_t(e)`

### structural based objective

1st-order proximity as in LINE. 

- `w_uv log p(v^s | u^s)`
  - weight times log probability of target embedding given source
- a node "predicts" its neighbor/target
  - reminds of the asymmetric transitivity paper
- softmax function

### text-based obejctive

three combinations of a similar form

1. `w_uv log p(v^s | u^t)`: text ebd predicts structural ebd 
1. `w_uv log p(v^t | u^t)`: text ebd predicts text ebd
1. `w_uv log p(v^t | u^s)`: similar

weighted sum of the above three terms

## context-free embedding via CNN

1. given word sequence (length `n`), extract the embedding (dim `d'`) for each word and concat them into a 2d matrix
  - matrix dim: `n x d`
  - row: embedding, column: word
2. convolution of the matrix using filters `d x l x d'`
  - `d` filters
  - output dim: `d x n` 
3. max-pooling and tanh
  - column-wise max-pooling to make sure output vector is of length `d`
  - in contrast to dynamic pooling mentioned [here](http://www.aclweb.org/anthology/P14-1062), where **max-k** values are extracted

## context-aware text embedding

question: given two "convolutionalized" matrices from two text pieces, how to derive two vectors for each piece s.t.:

1. the vectors are of the same length
2. they "affect" each other's representation: information from the two input items can directly influence the computation of each other's representations

using the paper [Attentive Pooling Networks](https://arxiv.org/abs/1602.03609)

basic idea:

- given input `P` and `Q` (each item respectively)
- add interaction between them by `F=tanh(P^T A Q)`
- derive importance vectors from row and column repectively via pooling, `g^p` and `g^q`
- normalize `g^p` and `g^q` using softmax (into probabilities)
- perform pooling using `P a^p` and `Q a^q` (weighted sum)

# comment of the paper

- why two sets of embedding? one for structure and one for text
  - why not just text embedding and combine it with the structural information?
- experiment not very strong
  - for node classification, only cora dataset and does not beat it strongly

# learned

- derive text embedding using CNN and pooling
- attentive two-way pooling
  - for *pair-wise* ranking and classification (for example tagging?)
  - `P a^p` part is clear
  - `F=tanh(P^T A Q)` and row/column pooling is confusing
- context-aware node embedding 
  - leads to to think aspect/topic-aware node embedding
  - not edge wise (local) but broader sense
- from experiment:
  - structural + text is better than either pure structural or pure text
  - attention helps

## some note on attentive pooling

traditional method for pair-wise ranking/classification: 

- CNN/RNN + max-pooling for representation learning

however, is max-pooling sufficient? can we fine tune the pooling process? 

the goal is to fine tune the pooling process (let the pooling be aware of the other input)

however, the reasoning behind method is unclear.

# thinking 

- interacts with vertex? why not interacts with topic or aspect?
  - via topic transformation? 

# question

- how to derive the node's embedding if context is absent?
  - input empty document?
  - for node classification, this might be a problem