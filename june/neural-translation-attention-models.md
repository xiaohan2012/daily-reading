# google' multi-lingual neural machine  translation


## goods

- zero-shot translation: example translate Korean->Japanese **without** ever seeing Korean->Japanese training data
- 


## tricks

- prepending "language token" at the begining of the input sentence to denote the target language
  - for example, "<2es>" for "to Spanish".
  - can we do similar things for music? multiple instruments?


# attention models

- in seq2seq, decoder can only refer to the previous and latest vector
  - however, RNN has problem remembering the first words (because of the long distance), which can be important
  - can be seen as a way to add **"memory"** to the NN (there are other methods for memory augmentation)
  - the longer the sentence, the harder to translate
- attention models allow it to refer to all previous vectors
   - *weights* are assigned for each previous vector by **scoring function**
   - the larger the weight, the more important
   - however, more computation cost because of more parameters
- this allows human to interpret the location of attention during the decoding process
  - implicit alignment (phrase-based MT)
  - similar to human translation process

after getting the weights for each piece of memory, they are combined by weighted sum and feed into the decoder. 


# scoring function

examples:

- inner	product between last embedding and internal memory vector
- bilinear form (`x^T W y`): interaction between `x` and `y`
- one layer of NN


# application of attention models

besides machine translation:

- image captioning (first CNN to embed the image, then an RNN to generate the words)
  - different words might "attend" to different regions of the image

# training


# reference

- [video](https://www.youtube.com/watch?v=IxQtK2SjWWM)
- [reading](http://www.wildml.com/2016/01/attention-and-memory-in-deep-learning-and-nlp/)