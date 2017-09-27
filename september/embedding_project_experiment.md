# experiment results

## experiment result for `kim_cnn`

softmax entropy as loss

1. p@1: ~30%
2. p@3: ~18%
3. p@5: ~14%

weird thing:

1. performnace **decreases**
2. training loss **increases**

possible explation: learning rate too high ([source](https://stackoverflow.com/questions/39868939/possible-explanations-for-loss-increasing))


## fastxml

1. precision at 1: 0.28439597315436244
2. precision at 3: 0.194910514541387
3. precision at 5: 0.15000000000000002
4. precision at 10: 0.10486577181208054

## PFastreXML

1. precision at 1: 0.2785234899328859
2. precision at 3: 0.1977069351230425
3. precision at 5: 0.1545302013422819
4. precision at 10: 0.10696308724832215

##  kimcnn + logistic entropy

1. p@1: 0.57
2. p@3: 0.38 
3. p@5: 0.29


# KISS (keep it simple and stupid)

- considering all labels (regardless of label refrequency)

# sep 18

misunderstanding: in order for the combined approach to work, data in validation set should also be "trained" to get the embedding. 

however, the labels to the validation set should be hidden. 

so next step: modify kimcnn to disable certain input data during training. 

# sep 19

get some inspiration from *Revisiting Semi-Supervised Learning with Graph Embeddings*

following sep 18, previous thinking on joint training is letting the unsupervised training signal flow to the cnn module. 

however, this complicates things. 

a simpler approach is:

- design another vector from the node embedding for classfication
- and let the output layer decide which part to give more emphasize

also, learned one training method for this kind of joint learning:

- alternate the trainining on each loss function separately while fixing parameters from the reminaing parts

for example, 

1. update parameters of the cnn part while fixing node embedding
2. update node embedding (cnn parameter does not affect)

# Sep 22

hack for missing placeholder value:

- just add some non-sense value for the missed placeholder

however, during graph training, it concats network embedding and text embedding. this makes no sense.

# Sep 23

we need one dummy training example, with non-sense words and non training labels, because even during graph training, label training needs input, weird. 

BTW, can I give a simple example that reproduces the same error. 

# Sep 25

at iteration 2200:
- `kim_cnn` achieves:
  - p1: 54% 
  - p3: 37%
  - p5: 28%

- `combined` 2000:
  - p1: 53%
  - p2: 36%
  - p5: 27%

one difference: training accuracy is much higher for `kim_cnn` than `combined`


# Sep 26

- use pretrained node embedding
- memory keeps increasing for combined model
  - possible reason: memory leak
  - is it because of deepwalk?

memory profiling tools:

- https://github.com/tensorflow/tensorflow/issues/492
- https://github.com/yaroslavvb/memory_probe_ops
- https://github.com/yaroslavvb/memory_util


# Sep 27

no need to k-fold cross validation (used for small dataset)

usually, split it into train/dev/test dataset. 

