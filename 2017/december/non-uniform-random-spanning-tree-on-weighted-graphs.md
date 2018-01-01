# non-uniform random spanning tree on weighted graphs

http://www.sciencedirect.com/science/article/pii/S0304397598003259

# main result

given some weighted graph, if we define the transition matrix of some random walk by `p(i, j) = w(i, j) / w(i)`. 

then, using Broder's algorithm, the tree genereted is distributed by the product of the edge weight. 

# automaton concepts

- state, transition
- language: a sequence of states that the antomaton accepts
- accepts/recognizes: by running the state transition, it finally enters th state "SUCCESS" (terminates)

## example

parsing the string "nice"

![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a8/Fsm_parsing_word_nice.svg/440px-Fsm_parsing_word_nice.svg.png)

# main idea

using automaton theory (not sure why)

- alphabet: set of edges
- word: sequence of edges/alphabet elements, or a random walk sequence
- language of spanning tree, `L_i(T)`: finite walks that generate `T`
- recognizing automaton, `A_i(T)`: an automaton that regonizes `T`

# what I don't understand

**Example 1**

what's the state here? the subgraph is shown without indicating the vertex currently being visited?


**automaton**

what does it mean to recognize?

# next

- understand some background on automaton theory