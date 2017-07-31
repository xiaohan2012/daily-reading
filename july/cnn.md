# related concepts in CNN


- "filter": a small 2D/3D matrix, matrix entries are the filter parameters. The depth of the filter should be the same as the image. For image with 3 color channels, the depth is 3.
  - can be seen as shape detector (curve, circle, line, segments, etc)

- "convolve" operation: dot product between a image block and the filter parameter
  - if the resulting value is large, it means the receptive field has such shape associated by the filter. 

- receptive field: the image block that a filter applies upon

- convolution layer: apply k filters to the image. Each filter generates a new "image" of certain depths (called activation/feature map). So together, it generates k feature maps (or 2D image of depth k)

- stride: how fast the filter moves. If stride is k, it moves k pixels a time.

- pooling: from a feature map to one real number
  - example, max-pooling, takes the max value in the feature map