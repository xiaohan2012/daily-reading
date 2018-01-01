# Efficient Algorithms for Public-Private Social Networks

a social nework consists of:

- a public network `G`: visible to every one
- private networks `\{G_u\}` for each user `u`: visible only to `u`
  - in other words, each user has its own view of the network
  - private networks might consist: a user hide his/her friends or private groups

## goal

how to compute nodes' level properties wihtout computing from scratch?

or computing node `u`'s properties using time `O(poly(G_u))`. 

## example challenge: recommendation at user-level in pp network:

- in order to preserve privacy, one can run the recommendation algorithm on public network only
- however, users with large private networks won't benefit
- further, for such user, it's not wise to re-run the algorihtm on the public network and user's private network from scratch



## problems it approaches:

- sketching: for approximate neighborhood function
- sampling: all-pair shortest path distances, node similarities and correlation clusrtering

