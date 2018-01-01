# `defs.h`

- `ASSERT_INFO` and `ASSERT` macro
- `ERROR`: exit with error message
# `gadget`

- `sb_tree`: size-balanced tree
- `disjoint`: disjoint set (union-find-delete structure)
- `heap`: min heap
- `treap`: tree + heap, the rank-order tree to calculate node's rank
  - it's tree abtractly. internally, it's a vector
  - related to node's rank


# `glist`


- `head_` and `tail_`: the head and tail of each `O_k`
- `node_`: the linked list
  - type `core::GLIST::ListNode`: bidirectional linked list
  - `rem`: `deg^{+}`
  - `ext`?

- variable `core` is a `vector<int>` passed as a referece into `ComputeCore`. it stores the core number


## questions

- how to use namespace? 
- `class GLIST final: public CoreMaintenance {`: what is `CoreMaintenance`?
