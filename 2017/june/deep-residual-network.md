# deep residual network

# observation

simply stacking more and more layers? gives worse and worse result.

- shallow network  vs deep network
  - copy layers in shallow networks to deep one
  - for the rest layers, make them identity
  - should not give the worse result,
  
# approach

given two layers `H(x)`,

- instead of fitting the output,
- fit the input `x` plus some fluctuations/residual `F(x)`
  - `H(x) = F(x) + x`


why deep?

- assumption: the deeper, the more powerful/expressive
  - **strange assumption**
- also, the more deeper, the fewer need for man filters, good for time complexity 
  - in other words, the depth matters more


# learned

- residual network means fitting input plus residual
  - my understanding: as a way to control the learning/optimization, instead of "going wild"
- VGG style: spatil size / 2 => \# filters x 2
- learned features can be transferred to other tasks such as object detection, tracking, etc
  - how to transfer?
