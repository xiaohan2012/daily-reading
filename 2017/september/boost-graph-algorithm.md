# overview

- graph with property (for example edge weight)
  - custom/standard property field
- run `bfs` and `dijkstra` on such graphs
  - use `record_distance` and `record_predecessor`
- lambda expression in c++ (since c++11)

# bfs

## distance

```c++
#include <boost/graph/breadth_first_search.hpp>
#include <boost/graph/visitors.hpp>

 array<int, 4> d {{0}};

  // bfs visitor consists of a list of visitors
  // for visitor list, refer to http://www.boost.org/doc/libs/1_46_1/libs/graph/doc/bfs_visitor.html
  // using make_pair
  boost::breadth_first_search(g, topLeft,
      boost::visitor(boost::make_bfs_visitor(boost::record_distances(d.begin(), boost::on_tree_edge())));
```

1. `boost::make_bfs_visitor` needs to be wrapped by `boost::visitor` to pass to `boost::breadth_first_search`
   - **named parameters**: `boost::visitor` just name the value returned by `make_bfs_visitor` to be "visitor"
1. use `property_map` if graph size is not known, now we use `boost::array`
1. `boost::on_tree_edge` defines the **event type**
   - record distance when the event `tree_edge` is fired (found new node)
   - any other event for `boost::record_distances`? yes, we can update the distance when old nodes are found as well, but that's not shortest distance
1. `include` relevant headers


## predecessor

change `boost::record_distances` to `boost::record_predecessors`

## pairing up visitors

pass `std::make_pair(boost::record_distances(...), boost:record_predecessors(...))` to `boost::make_bfs_visitor`

# lambda expression C++

usually `[ captures ] ( params ) -> ret { body } ` or `[ captures ] ( params ) { body }`

1. first form: return type is defined
2. second form: return type is induced
3. `captures`: variables to use apart from `params`

## examples 1

```c++
 std::for_each(v.begin(), v.end(), [](int i) { cout <<  i << endl;});
```

just print out the values in `v`

## examples 2

```c++
void f(std::vector<double> v, const double& epsilon) {
    std::transform(v.begin(), v.end(), v.begin(),
        [epsilon](double d) -> double {
            if (d < epsilon) {
                return 0;
            } else {
                return d;
            }
        });
}
```

- return type is `double`
- `epsilon` is the `captures`
- `std::transform` just `map` in python

# graph property

```c++
typedef boost::adjacency_list<boost::listS, boost::vecS,
  boost::undirectedS, boost::no_property,
  boost::property<boost::edge_weight_t, int>> weighted_graph
```

1. `no_property` (4th arg) is for node
2. second `property` (5th arg) is for edge
   - `boost::edge_weight_t` key type
   - `int` value type

## intialize weighted graph

```c++
  array<int, 4> weights{{2, 1, 1, 1}};

  weighted_graph g{edges.begin(), edges.end(), weights.begin(), 4};
```

just `weights.begin()` is fine, why?

## run dijkstra

```c++
  boost::array<int, 4> directions;
  boost::dijkstra_shortest_paths(g, bottomRight,
                                 boost::predecessor_map(directions.begin()));
```

- `boost::predecessor_map`: helper for named argument

note that weight property is automatically recognized

# user-defined property

not using `boost::property`, but our own struct

```c++
  struct edge_properties
  {
    int weight;
  };
  typedef boost::adjacency_list<boost::listS, boost::vecS,
    boost::undirectedS, boost::no_property,
    edge_properties> graph;
```

## initialization

```c++
boost::array<edge_properties, 4> props{{2, 1, 1, 1}};

graph g{edges.begin(), edges.end(), props.begin(), 4};
```

## dijkstra

needs to specify weight property

```c++
boost::predecessor_map(directions.begin()).
    weight_map(boost::get(&edge_properties::weight, g))
```

get `weight` from `g`  (wierd syntax...)

# random spanning tree

```c++
  boost::array<int, 4> predecessors;

  std::mt19937 gen{static_cast<uint32_t>(std::time(0))};
  boost::random_spanning_tree(g, gen,
                              boost::predecessor_map(predecessors.begin()).
                              root_vertex(bottomLeft))
```

- root needs to be specified after `predecessor_map` (wierd)


