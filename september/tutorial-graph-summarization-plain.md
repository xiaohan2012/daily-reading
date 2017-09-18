graph summarization/coarsening/aggregation: part 1

# goal 

find **a short representation** of a graph, usually a sparsified graph or a "summary"

# motivation/appliations

reduce data volume that enables:

- query efficiency 
- visualization (easier interpretation)
- compression (managable in memory or disk)
- "pattern" discoery

my note:

- ontology graph (understanding)
- product graph (entity resolution)

# challenges

- how to evaluate a summary?  depends on method and application
  - compression based: reconstruction error
  - query efficiency and accuracy
  - community structure
  - "quality" application specific

# grouping-based approach

merge nodes into super-nodes and add super-edges

variants:

- minimizing reconstruction error
- preserving *"structural"* property
- preserving *"diffusive"* property
  - first eigen value of the matrix is not changed much
- group nodes of same type in heterogenous graph
  - application: entity resolution (product network)

# simplification/sparsification-based approach

remove less *"important"* nodes or edges

- node/edge sampling
- graph sketches


# compression-based

MDL-based approach: 

minimize `L(D) + L(M|D)`

- `D`: summary
- `M`: input data

simple and good summary

## vocabulary-based summarization

graph-vocabulary: star, line, bipartite, etc

https://arxiv.org/abs/1406.3411

## graph densification

http://www.kdd.org/kdd2016/subtopic/view/scalable-pattern-matching-over-compressed-graphs-via-dedensification

# influence-based summarization

short representation of **information flow**

[spine](https://bbuseruploads.s3.amazonaws.com/mmathioudakis/spine/downloads/spine.pdf?Signature=VjF5NaSUVi9mN008u4%2F%2BkF%2BWWBU%3D&Expires=1505757667&AWSAccessKeyId=AKIAIQWXW6WLXMB5QZAQ&versionId=null&response-content-disposition=attachment%3B%20filename%3D%22spine.pdf%22)


# frequent pattern

motif simplification, e.g, fan, connector, clique, for visualization

Dunne, Shneiderman, 2013


a lot of refernences and comparison: **page 71**