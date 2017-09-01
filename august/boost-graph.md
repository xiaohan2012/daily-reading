https://theboostcpplibraries.com/boost.graph

- graph creation using adjacency_list
  - print node/edge
- using different selectors to init graph
- edge property (weight, etc)
- run algorithm such as bfs, dfs on graph

# adjacency list graph

```c++
boost::adjacency_list<> g; // graph
boost::adjacency_list<>::vertex_descriptor v; // vertex
boost::adjacency_list<>::edge_descriptor e; // edge

v = boost::add_vertex(g); // add vertex
std::pair<boost::adjacency_list<>::edge_descriptor, bool> = boost::add_edge(g); // add edge, bool indicates whether edge is added successfully or not

boost::adjacency_list<>::vertex_iterator vi; // vertex iterator, used by boost:vertices
boost::adjacency_list<>::edge_iterator ei; // edge iterator, used by boost:edges
```

`std::pair<boost::adjacency_list<>::vertex_iterator, boost::adjacency_list<>::vertex_iterator>  = boost::vertices(g)` returns pair of iterators (begin and end)

a quick way to print vertices or edges

```c++
  pair<edge_iterator, edge_iterator> es = boost:edges(g);
  std::copy(es.first, es.second,
       std::ostream_iterator<edge>{
         cout, "\n"
           });
```

more one [istream_iterator and ostream_iterator](http://en.cppreference.com/w/cpp/iterator/istream_iterator/istream_iterator)

# graph selector

`boost::adjacency_list<arg1, arg2, arg3>`

- `arg1`: container for edge, example: `boost::setS`
- `arg2`: container for node, example: `boost::vec`
- `arg3`: directed or not, `boost:undirectedS` or `boost::bidirectionalS`

for exmaple `boost::adjacency_list<boost::setS, boost::vecS, boost::undirectedS>` gives undirected graph disallowing duplicate edges

correspondingly, the edge type or iterator type needs to change:

`boost::adjacency_list<boost::setS, boost::vecS, boost::undirectedS>::edge_descriptor`

## adjacent nodes and edges

get adjacent nodes: use `adjacency_iterator`

```c++
graph_type::adjacency_iterator it1, it2; // sensitive to graph_type
tie(it1, it2) = boost::adjacent_vertices(vertex, g); 
```

get in/out edge: use `out_edge_iterator`

```c++
adj_ugraph::out_edge_iterator oe1, oe2; //sensitive to graph_type alo
tie(oe1, oe2) = boost::out_edges(2, g1);
```

## create graph by edges

```c++
array<pair<int, int>, 4> edges {{
    make_pair(0, 1),
    make_pair(1, 2),
    make_pair(2, 3),
    make_pair(3, 4)
    }};
graph_type g2(edges.begin(), edges.end(), 4);  # needs to pass the number of edges, why?
```