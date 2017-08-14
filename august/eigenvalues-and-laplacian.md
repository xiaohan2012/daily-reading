# notations

- unnormalized laplacian matrix:  $` L  `$
- normalized laplacian: $` \mathcal{L} `$
  - 1 if $` u=v `$
  - $` - \frac{1}{\sqrt{d_u d_v}} `$ if $`u \neq v `$
- diagonal of $` \mathcal{L} `$: `$ T `$
- other forms of $` \mathcal{L} `$
  - `$ T^{-1/2} L T^{-1/2} `$
  - `$ I - T^{-1/2} A T^{-1/2} `$
    - example: for `$k`$-regular graph, `$\mathcal{L}=I - \frac{1}{k}A`$
- Rayleigh quotient: `$\frac{<g, \mathcal{L}g>}{<g, g>} = \frac{\sum\limits_{u ~ v} (f(u) - f(v))^2}{\sum_v f(v)^2 d_v}`$
  - `$ g=T^{1/2}f`$