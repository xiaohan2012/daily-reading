# Efficient Algorithms to Optimize Diffusion Processes under the Independent Cascade Model

proposese a general problem definition that captures different diffusion optimization problems

# problem

consider IC model, we are allowed to manipulate the edge probabilities by changing it from `p_{uv}` to `p_{uv}^{'}` (called "action"). 

the problem is: we are allowed to take actions under certain cost `B` so to maximize or minimize the (expected) size of the cascade. 

this generalizes to specific problems:

1. assume a dummy node `d` connected to all the nodes and `p_{dv}=0` initially. and an action is defined by making `p_{dv}^{'}=1`. and we are allowed to make such changes on `B` edges to maximize the spread. this is the same as influence maximization problem
2. the action is making `p_{uv}^{'}=0`, it's like cut-off the communication to reduce rumor spread
3. the action is to *increase* `p_{uv}` to maximize the spread of influence

