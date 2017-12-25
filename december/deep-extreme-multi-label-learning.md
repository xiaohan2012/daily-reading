# Deep Extreme Multi-label Learning, axiv

# basic idea

training:

- learning label embedding
- train regressor to get embeddings that are close to the label embedding


prediction:

- KNN based

# what might be improved

- label graph construction (no weight is considered)
- label embedding learning method (DeepWalk is used)
- experiment result is not very convincing

# learned

- average sum of label embedding vectors as the training signal