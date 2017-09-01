# Deep Learning for Extreme Multi-label Text Classification, SIGIR 2017

adaption from textCNN by Kim. 

main adaptations:

1. loss function: binary cross-entropy on sigmoid
   - sould be improved here

2. bottle-neck layer: one hidden layer between pooling and output
   - to reduce memory because `L` (label dim) is large
   - one more layer of non-linearity

3. dynamic-pooling: instead of max-pooling, use max-`k` pool
   - intuition: just one max loses information
   - diving the sentence into `k` chunks, take the max from each chunk


