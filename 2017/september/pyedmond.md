# intro

I tried to wrap a C++ implementation of edmond's optimal branching algorithm.

# learned

- `BOOST_FOREACH`: in boost/foreach.hpp 
- `boost::python::extract` to extract the c++ typed value from python object
- `boost::python::tuple` also supports integer indexing

# observation

the main bottle neck is spent on converting the graph (80% of the time)

- 20% get the edges
- 60% build the graph

the actual computation only takes 16.2%.	

I asked the question in graph tool maillist: http://main-discussion-list-for-the-graph-tool-project.982480.n3.nabble.com/Integrating-edmond-s-algorithm-in-boost-graph-with-graph-tool-td4027361.html

# trick for `graph_tool`

- `Graph.edges()` is slower than `Graph.get_edges()`
- `Graph.get_edges()` returns `np.array` (size `m` by 3)