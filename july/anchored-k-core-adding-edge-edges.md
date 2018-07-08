# Can We Create Large k-Cores by Adding Few Edges?

problem: 

- given graph, budget $`b`$, core number $`k`$, vertex set size $`p`$
- can we add $`b`$ edges such that $`\ge p`$ nodes have core number $`\ge k`$?

main results: 

- $`k \le 2`$, poly, $`k \ge 3`$, np-hard
- when $`k=3`$, $`W[1]`$-hard parametrized by $`b+p`$
- $`W[1]`$-hard parametrized by $`k+p+b`$
- FTP by $`tw+b+p`$, where $`tw`$ is tree width

note: tree width is usually used for parametrized complexity analysis
- [the wikipedia definition](https://en.wikipedia.org/wiki/Treewidth): looks complicated, what's the intuition?
- some examples:
  - complete graph has $`tw=n-1`$
  - tree has $`tw=1`$


interesting direction:

- do parametrized complexity analysis for our problem
  - propose FTP algorithm?
  - prove hardness