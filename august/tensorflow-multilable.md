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