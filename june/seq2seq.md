# problems with existing models

## fully connected perceptron

- length of input and output are fixed: cannot be adapted to arbrary length input (machine translation)
- 

## RNN

- one-to-one correspondence between input and output units
- hard to train:
  - vanishing gradient
    - cause: traditional RNN *overides* the previous hidden state completely
    - solution: LSTM -- add the previous hideen states to the current one
  - exploding gradient
    - NN becomes sensitive to pertubation and gradient becomes very large
    - solution: clipping (truncate it if it's too large)


## main contribution

- simple model based on LSTM: let the model predict the rest
  - iteratively feed the previous output into the next input.
  - the first input is simply a literal denoting START
  - but when to stop? some STOP symbol?
- deep LSTM: multiple layers of LSTM


## representation

- embedding for the sequence can be get from the last column layers of the input sequence.
- interesting to visualize the representation of different but similar or similar but different sentences.


## parameter tuning

- learning rate: decrease at the end
- initial guess
- clip the gradient


## questions

- how does LSTM work?
- why use multiple layers of LSTM?