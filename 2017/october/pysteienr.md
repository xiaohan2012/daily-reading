- `boost:dijkstra_shortest_path` have overloaded function
  - one way to pass in predecessor is `&predecessors[0]`

- `boost::array::begin` and `std::vector::begin` seem to return different things, while `&std::vector[0]` matches the type
  - encountered in `boost::record_distance`

- what's the benefit of `boost::property_map` compared to `std:unordered_hashmap`

- use directly `INT_MAX`

- `boost::dijkstra_shortest_paths` is general than I thought, it supports custom definition of weight comparison and weight combination (default is `+`)

