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