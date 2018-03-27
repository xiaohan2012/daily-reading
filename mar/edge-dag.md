
# claims

## claim 1

~version 1~ (wrong)

~given an new edge node, the set of dependent edges $`(u, v)`$ are those:~
   - ~adjacent to one of the promoted nodes, $`u`$~
   - ~and has $`core(u) \le core(v)`$~

~version 2~ (wrong)

given an new edge node $`V_p`$, the set of dependent/necessary edges $`(u, v)`$ are those:

   - adjacent to one of the nodes from core-guided BFS starting from the promoted nodes $`V_p`$
     - the BFS only visits nbrs with equal or higer core number
   - and has $`core(u) \le core(v)`$


the intuition for the changing part is: promoted node depends on its equal-or-higher core neighbors, 

- such neighbors can already be promoted by previously added edges
- and the recursion goes on 

a bad example:


    a --- b
    |     |
    |     |
    |     |
    c --- d
    | \
    |  \
    |   \
    e --- f



consider adding edges $`(a, d), (b, c), (e, d), (d, f)`$

             a b c d e f
    init     2 2 2 2 2 2
    (a, d)   2 2 2 2 2 2
    (b, c)   3 3 3 3 2 2  <- a, b, c, d promote, depends on $`(a, d), (b, c)`$
    (e, d)   3 3 3 3 2 2
    (d, f)   3 3 3 3 3 3  <- e, f promote, depends on only $`(e, d), (d, f)`$

~after adding $`(d, f)`$, $`{e, f}`$ promotes to 3, however, the dependent edges are **all** edges, not just $`{(e, f), (d, f)}`$~


a good example:


         - a (inside a quasi-clique of 5 nodes with core number = 2, other nodes omitted)
       /
      / b --- c
     |  | \   |
     |  |  \  |
      \ |   \ |  
        d --- e


edges being adding:

1. edges to make the quasi-clique a full clique, now its core is 4
2. $`(a, c)`$: now $`{b, c, d, e}`$ becomes core 3, however depending on edges added at step 1

lessons learned:

- whether a node needs higher order edges depends on if its degree within the promoted node is enough

for example, $`b, e`$ have enough edges from peers already, however, $`d, c`$ both need one more (which comes from a)

in the previous example, $`c, d, e, f`$ all have enough edges already, so no need to traverse. 