# core maximization -- incremental update

# update subcore

given affected nodes, need to do either:


**merge them to higher core(s)**

example: 4-clique (a-d), 4-clique (e-h) and quasi clique(1-4) where edge (1, 4) is missing, also edges (1,a) and (2, e) are connected

adding edge (1, 4) will merge all cliques into one sub core

**create a new core**

if there are no affected subcores, then we need to create a new core.


information to update:

- `nc.nodes` 
- `nc.usable`

# update `B<` and `B=`

due to previous step, both `B=` and `B<` should consider:

- the newly merged subcore: need to add the entries
- the previously removed subcore(s): need to remove the entries

however, where to find the `nodes` and `sc_ids` to remove? use the old `sc.size`
