# goal

problem: given gene, protein, we don't know the full interaction among them. 

to learn it, we need data. 

to generate data, we do experiment. 

then, which experiment to do?

# simple setting: boolean network

the network is a DAG, parent gene determines if child gene is repressed (0) or activated (1). 

an experiment is a list of genes to perturb and values on them (0 or 1) and the outcome is state of the other genes. 

goal: given a set of candidate networks and a pool of candidate experiments, select the best candidate experiment. 

given an experiment $`e`$, it will produce an outcome (deterministic) $`x`$ on a give network. 
then different networks will possible give different outcomes, $`\{x_1, x_2, \ldots, x_{k}\}`$.

one entropy-based measure is treating $`x`$ the variable and estimate its entropy based on fraction of networks that give $`x`$.
