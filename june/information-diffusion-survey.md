# Information diffusion in online social networks: a survey

https://dl.acm.org/citation.cfm?id=2503797

subtopics: topic detection / diffusion modeling / identify influential individuals

# diffusion modeling

## network reconstruction: explanatory

problem: given a complete activation sequence, infer the cascade structure and optinally the graph structure

- NETINF: static graph
- NETRATE: static graph, models the transmission function (continues)
- INFOPATH: dynamic network

### data acquisition bottle neck 

due to API restrictions

- [7] studies how sampling strategy affects the discovery of information cascade 


## predictive models

problem: predicting how a specific diffusion process would *unfold* in a given network

### predict the graph of diffusion

cascade models: IC, LT, and asynchronous version of both [42], where parameters can be learned

### non-graph based approach

time-series prediction