
# goal

learn word representation that is optimized for a given text classification task

motivation:

- we need to perform classification task 
- however, documents are partially labeled, how to utilize the unlabled part?
- supervised + unsupervised learning

 
# input and output

- input: partially labeled text corpora
- output: embedding of the words
  - does the label have embedding?

constructing a partially labeled text corpora into 3 networks:

1. word-word network: weight by co-occurence frequency
   - words' embedding to be learned
2. word-document network: weight frequency of word occuring in document
   - document embedding aggregated from words in it
3. word-label network: frequency of word occuring in document of certain label
   - label is the training signal

# objective function

three parts:

- `\sum_{ij in E_ww} w_ij \log p(vi | vj)`
- `\sum_{ij in E_wd} w_ij \log p(vi | dj)`
- `\sum_{ij in E_wl} w_ij \log p(vi | lj)`

for `\log p(vi | vj)`, the softmax function

# summary

paper is not very well-written, not very clear to be honest, for example:

- does label have an embedding?

- why construct three networks?
  - the word-label one is confusing
  - why not predict the labels based on the document vector?


# further reading

- [cnn for text classification](http://www.aclweb.org/anthology/D14-1181)
  - [implementation in tensorflow](https://github.com/dennybritz/cnn-text-classification-tf)
  - [blog post](http://www.wildml.com/2015/12/implementing-a-cnn-for-text-classification-in-tensorflow/)