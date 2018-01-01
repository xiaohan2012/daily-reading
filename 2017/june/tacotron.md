# CBHG

- `K` sets of 1D convolutional filters.
- each set corresponds to filters of with `k`. (1...k grams)
- each set is of size `C_k`.


# pipeline

encoder:

1. input: a character sequence (one-hot vectors)
2. embedded into continous space
3. "pre-net": non-linear transform
  - essentially fully connected layers with dropout
  - how? input sequence has varying length.  applied to each embedded vector
4. CBHG encoder: extract sequence representations
  - consists of convolutional layers and RNN on top
  - the convolution part is similar to the CNN for sentiment prediction, to extract contextual information


decoder:

1. input: "<GO>" frame, similar to START symbol in MT
2. pre-net: similar purpose as encoder
3. attention RNN:
  - input: current state vector, all encoded memory vectors
  - output: weighted sum of encoded vectors where weight is by the scoring function (taking current state vector and one memory vector )
4. decoder RNN:
  - input: attention RNN output and previous state vector (concatenated)
  - output: new state vector and target 
  - with residual connections
  - the target is 80-band mel-scale spectrogram **(why?)**
5. post-processing
  - convert the seq2seq target to a target that can be synthesized into waveforms
6. waveform synthesis
  - Griffin-Lim algorithm


# questions

- [sample rate, frame rate](https://sound.stackexchange.com/questions/5022/how-many-samples-are-in-a-frame)
- why is it faster?
- what is mel-scale spectrogram?
  - [mel-scale, perceptual scale](https://en.wikipedia.org/wiki/Mel_scale)  