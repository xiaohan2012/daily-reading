# sampling-importance resampling

we want to sample from $`\pi(x)`$, which is not easy to sample from. 

instead, we do the following:

1. sample from  proposal distribution $`q(x)`$, 
2. resample the samples (to reduce for the bias) with probability proportional to $`\frac{\pi(x)}{q(x)}`$

# how to choose $`q`$ to make it work well?



# resources

- http://astrostatistics.psu.edu/su14/lectures/cisewski_is.pdf
- http://onlinelibrary.wiley.com/doi/10.1111/1467-9469.00360/pdf
- http://math.tut.fi/posgroup/heine_fusion05a.pdf
