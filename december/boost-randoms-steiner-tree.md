# learned


# random number generator for rand span tree

`rng` passed to `weighted_random_out_edge_gen<Graph, WeightMap, Gen> random_oe(weight, gen);` is as simple as `std::mt19937 prng { 42 };`

# init `PropertyMap` from iterator

    boost::make_iterator_property_map(predmap.begin(), get(boost::vertex_index, g))

# most important lesson

- `graph_tool` is hard to integrate
- why not produce a minimum working example from scratch?