# blossom's algorithm to find maximum matching

- https://www.cs.dartmouth.edu/~ac/Teach/CS105-Winter05/Notes/kavathekar-scribe.pdf
- https://en.wikipedia.org/wiki/Blossom_algorithm (with good illus)


# maximal and maximum

denote `M` as a matching

- maximal matching: no more edges can be added (can be multiple maximal matchings)
- maximum matching: the maximal matching that gives the *maximum* size (num of edges)

# finding maximium matching

greedily adding one edge until no more edge can be added

# blossom algorithm

concepts:

**augmenting path**: a path `P` s.t.

  1. its two end points are unmatched/exposed
  2. the edges are alternatinly in and not in `M`

augment a path `P` = `(M \ P) \cup (P \ M)`:

1. remove edges in path that are in `M` from `M`
2. add edges in path that  are not in `M`

by augmenting a path, the two unmatched nodes are now matched

**Berge's Theorem**: `M` is maximum if and only if there is no augmenting path

## how to find the augmenting path?

using the idea of blossom.

didn't understand

## time complexity

- `O(V^2 E)`


# other methods

- by Vazirani: https://www.cc.gatech.edu/~vazirani/new-proof.pdf
- 