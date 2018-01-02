# list of np-hard problemss

reference: http://jeffe.cs.illinois.edu/teaching/algorithms/2009/notes/21-nphard.pdf

# circuit satisfiability

given a boolean circuit with input variables (true,false) and `And`, `Or`, `Not` gate, decide if there is a combination of input variable values that evaluates to `True`. 

# formula satisfiability (SAT)

just transform the formula to its equivalent boolean form. 

# 3SAT

conjunction normal form: 

- *conjunction* (AND) of several clauses where each is a *disjunction* (OR) of several *literals* (input variables or its negation)

- 3CNF: three literals per clause
- 3SAT: SAT of 3CNF form

reduce circuit satisfiability to 3SAT

- for single input gate, add two dummy variables
- for two-inputs gate, add one dummy variable
- to be continued

# Maximum Independent

given a graph: 

- independent set: set of nodes with no shared edges
  
- each node is a set and covers a list of edges. 
- two nodes are independent if there do not overlap in their contained elements

*maximum independent set problem* the size of largest independent set. 

reduction from 3SAT. build graph by:

1. create a node for each literal formula
2. connect two nodes if they are in the same clause or are the opposite of the same literal
   - the first type of edge ensures that we only need to select one of the literals in the same clause to be true (the clause evals to true)
   - the second type of edge (the value of variable cannot contradict with each other)

given a formula of `k` clauses, it's satisfiable if and only if there is an independent set of size `k`. 

- just evaluates the selected node to true
- not just 3SAT, any SAT is fine I guess

# clique

finding the max clique (in size) in a graph

reduction from max independent set: 

- create edge complement graph `G^{'}` (there is an edge in `G^{'}` if there is not an edge in `G`)

an independent set of size `k` in `G^{'}` corresponds to a clique of size `k` in `G`

# vertex cover

