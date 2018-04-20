# Mapping the Invocation Structure of Online Political Interaction

https://arxiv.org/pdf/1802.09597.pdf

# research question

whether online political interaction consists of:

1. opposing sides who engage with each other,
2. well-separated clusters who are isolated in “echo chambers” or “filter bubbles” 

## terms

- political spectrum: left or right (wing)

use US presendential election as an example

# main finding

- increasing linkage between the two sides (left and right) as the election approached 
  - Figure 3 and 5
- asymmetry of left-right and right-left link patterns  


validated from the user-level (more fine-grained)


# invocation graph

- node: domain (e.g. news site)
- edge: (directed) A -> B if user $`u`$ uses page $`A`$ to reply to a post/tweet containing $`B`$
- edge weight: count of such reference

features:

- reader decided (instead of author)
- conversation oriented (not like hyper-links)

# embedding invocation graph in political spectrum

each node/domain is associated with a scalar value (closer to zero, more "leftness", closer to one, more "rightness")

what they used:

- conditional probability $`P(x | T)`$ ($`P(x | C)`$)  that $`x`$ is tweeted by a user who also retweeted Trump/Clinton's official tweet on the same day, 
- score $`s(x) = P(x | T) / (P(x | T) + P(x | C))`$, the larger, the more Trump

Figure 2 gives an idea who support Trump/Clinton. 

# out link distribution

- given node $`x`$, it's weighted average of the out neighbors' $`s(x)`$. 
- minused by the global out link distribution

# leanrned

- the finding on US election that increasing linkage between the two sides as election date approached
- techniques used, domain graph, spectral embedding, out-link distribution, link distance (diff of spectrum embedding)
- the need to validation of domain-level analysis using user-level analysis