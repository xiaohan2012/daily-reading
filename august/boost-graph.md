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