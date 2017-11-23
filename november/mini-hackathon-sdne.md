# Mini-hackathon: deep structural network embedding

goal

- SDNE or LINE in [keras](https://keras.io/) 
  - what's the time complexity
- classification on standard datasetn
- network reconstruction
- visualization on standard dataset and the label datasets

# runtime

## how to add edge-wise loss function

- use `merge` to get the difference
- define custom loss function to get the real loss (mean, square, etc )

refer to [this](https://github.com/palash1992/GEM/blob/master/gem/embedding/sdne.py)

# links

- [initialize embedding with values](https://github.com/fchollet/keras/issues/853#issuecomment-149644701)

## code and papers

[survey](https://arxiv.org/pdf/1705.02801.pdf)


- [SDNE, tensorflow](https://github.com/suanrong/SDNE)
- [LINE, C++](https://github.com/tangjianpku/LINE)
- [LINE, keras](https://github.com/VahidooX/LINE)
- [GEM, python](https://github.com/palash1992/GEM), a collection of algorithms
- [OpenNE, tensorflow](https://github.com/thunlp/OpenNE), a collection of algorithms by Tsinghua University


# learned

- before defining your own custom loss function, test it!

## a very series mistake that bugged me the whole day

input to the loss function is

- `true_output`: passed as the 2nd argument in `model.fit`
- `pred_output`: the output the model (not the input)
  - in my case, it's the reconstrudcted neighborbood, not the input node ids


## loss function argument's shape

must match.

in my case, the edge wise loss does not need `true_y`. 

so theoretically, `None` can be passed. 

however, because of this requirement, `np.array` with the same shape as `embedding_diff` need to be passed.

## regularizer

- add it the the layer definition
- https://keras.io/regularizers/

## setting zero entries to 1 and multiply non-zero entries by constant, `a`

just `v * (a-1) +1`

## `Lambda` layer

to add arbitrary transformation

## sparse input

not very easy in keras

## comment on sklearn `GridSearchCV`

- the model needs to have `fit`, `score` and `set_params` interface

## pre-training

pre-training should be done on autoencoder

# todo

- [ ] cross validation on the visualization of 20newsgroups
- [ ] tensorboard visualization of label embedding
- [ ] link prediction on test data
- [ ] write blog article

# questions

- what are `loss`, `decoding-layer-0_loss_1`, `decoding-layer-0_loss_2` and `lambda_1_loss`?
- where is `l2_param` reflected?
- for link prediction on grqc dataset, what if removing edges cause disconnected component?
  - also how to deal with directed edges?
- why grqc have 28980 edges in the paper while on snap, it only has half?