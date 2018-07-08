# utility


- [timeout](https://stackoverflow.com/questions/2281850/timeout-function-if-it-takes-too-long-to-finish)
  - multi-thread not supported..

# conda

- [export and clone environment](https://datascience.stackexchange.com/a/24096/33194)

# numpy/scipy

- sparse matrix point-wise division
  - can be achieved by `.multiply`, needs to "invert" the divident first by `div_m.data = 1 / div_m.data` and then `m.multiply(div_m)`
  - note that `m.data /= div_m.data` does not work