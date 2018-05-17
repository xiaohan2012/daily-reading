# applications of minimum steiner tree

## deploying telecommunication pipe/cable

http://homepage.univie.ac.at/ivana.ljubic/research/STP/


## marker gene identification for breast cancer

https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3481447/

gene marker: A genetic marker is a gene or DNA sequence with a known location on a chromosome that can be used to identify individuals or species (or some disease?)

- goal: identify gene marker for breast cancer
- observation:  disease/marker genes play a role in connecting differentially expressed (DE) genes in PPI networks
- approach: run randomized version of min steiner tree algorithm on the PPI network, intermediate nodes serve as the disease gene
  - randomization achieved by assigning random edge weights

Q:

- what are the features for the classifier?
- what does table 1 mean?

in the context of protein network, this problem is referred as *signaling pathway reconstruction*


## recommendation

### [Searching Steiner trees for web graph query](https://www.sciencedirect.com/science/article/pii/S0360835211003366)

- argues that treating each webpage separately is not enough because webpages are inter-linked
- problem: given a set of query words, find the set of webpages that contain the words and are inter-linked
  - all pages together should cover all the words
  - however, some pages may not cover a node at all (the steiner node), those that cover at least one node are the terminals
- further formulated as top-k steiner tree problem

### [Steiner Tree Based Recommendation System for Combination of APIs and IoT Devices](https://ieeexplore.ieee.org/document/8305980/)

goal: recommend mashup of APIs given user queries

a user query can be "a system monitors elderly people and emails their family if an emergency occurs"

a *directed* graph is built

- nodes: feature, IoT device, input/output (by device), API
  - feature can be provided by devices (see Fig 2 and 3)
  - among features, one feature can cover the functionality of another feature (alternative feature)
  - the user needs to break the query into features, for the example above, the features can be “wake-up detection,” “human presence detection,” and “sending email.”
- edges: relation between them
  - feature can be alternative to one another (so directed)
  - device has input and output nodes that provide features, etc
  - Fig 4

given some feature nodes as terminals, the recommendation algorithm finds a smal steiner tree. 

However, the tree needs to stick to certain rules therefore the algorithm is ad-hoc.
- can we contruct the graph such that the algorithm is agnostic about the rules?

### recipe recommendation

[Intelligent menu planning: recommending set of recipes by ingredients](https://dl.acm.org/citation.cfm?id=2390778)


## community detection

http://www.columbia.edu/~khl2114/files/74.pdf

