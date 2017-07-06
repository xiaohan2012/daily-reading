
# 9: Come-and-Go Patterns of Group Evolution: A Dynamic Model, KDD 2016

Group evolution (parts of social social research): understaning how groups take shape and evolve over time?

- temporal patterns of group evolution: spatial and temporal
- quit process/machanism: ignored by many research

## Novelty

Proposes a method that models group evolution process capturing:

- quit process and power-law holding time distribution in quit process
  - holding time: quit group time - join group time
  - SIR model gives exponential distribution
- non-diffusion mechanism for joining groups:
  - impulses in join process

Group joining process can be seen partly as a infection process. Joining group = get infected. 

## Model

Base model parameters:

- `J(t), Q(t), I(t)`: number of join/quit/in group until time t
- `N`: number of people
- group attractiveness: `beta` (can be seen as infection probability in SIR)
- holding time distribution parameter: `gamma` and `alpha`. the latter controls the shape of the distribution, can switch between exponential and lower-law, depending on `alpha` value.

Adding external impulses:

- `lambda\_i` for the strength of impulse at time `t\_i`

## Learned: 

- studying group evolution via epidemiology models
  - "quit" can be seen another form of "recovering" but follows a different holding time distribution compared to SIR model. 
- power-law decay and exponential decay:
  - [power-law](https://en.wikipedia.org/wiki/Power_law): a/(x^k), decreases slower because x^k increases slower than e^x. 
  - [exponential decay](https://en.wikipedia.org/wiki/Exponential_decay): 1/(e^x)
- learning problem formed as non-linear least squares, solved by Levenberg–Marquardt algorithm

## Related question:

- how frequently do people chat in the group overtime? Uniformly or with burst? How to predict it?
  - Maybe a different model? Like SIS? There is no quiting but being silent for a while. And again it can be infected. 
- what's the fraction of likes that are driven by the "following-the-crowd" mindset. 