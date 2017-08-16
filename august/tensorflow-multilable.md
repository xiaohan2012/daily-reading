# from multiclass to multilabel

1. `tf.nn.sigmoid` instead of `tf.nn.softmax`: classification
1. `tf.nn.sigmoid_cross_entropy_with_logits` instead of `tf.nn.softmax_cross_entropy_with_logits`: loss function
1. `tf.round` instead of `tf.argmax`: prediction

- [blog example](https://medium.com/towards-data-science/multi-label-image-classification-with-inception-net-cbb2ee538e30)
- [code example](https://github.com/BartyzalRadek/Multi-label-Inception-net/blob/master/retrain.py#L831)

# sigmoid function

1. `1 / (1+exp(-x))`
   - the larger the `x`, the closer to 1
   - the smaller the `x`, the closer to 0
   - 0.5 is the threshold between 0 and 1 by default


# computing precision and recall

using `tf.metrics.precision` and `tf.metrics.recall`. 

actually computes the "micro" version (takes into account of label imbalance). 

remember to initialize local variables as well because the above two functions using

`sess.run(tf.local_variables_initializer())`

see mu (my post)[https://stackoverflow.com/questions/45720291/failedpreconditionerror-while-using-tensorlfow-metrics-recall/45720460#45720460] 
for more

# where to put variable initializer

I mean this: `sess.run(tf.global_variables_initializer())`

- **after** all variables are defiend
- or **before** actual training begins

