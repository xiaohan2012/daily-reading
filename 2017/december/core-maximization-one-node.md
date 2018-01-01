# core maximization: one node version

# property

## non-submodular

example: 

- initial graph: $`(a-b-c-d)`$, $`(e, a)`$, `$(e, b)$`,  2-core
- edge 1: `$(e, c)$`, 2-core
- edge 2: `$(e, d)$`, 3-core


## non-supermodularity

example:

- initial graph: `$n$`-clique of nodes `$\{1, \ldots, n\}$`, `$n+1$`-clique of nodes `$\{n+1, \ldots, 2n+1\}$`
- `$E=\{(1, n+1), (2, n+1), \ldots, (n-1, n+1)\}$`, `$E^{'}=E \cup \{(n, n+2)\}$`
- `$e=(n, n+1)$`

- `$\Delta f(E + e) - \Delta f(E) = n-0=n$`
- `$\Delta f(E^{'} + e) - \Delta f(E^{'}) = n-n=0$`

therefore `$\Delta f(E + e) - \Delta f(E) > \Delta f(E^{'} + e) - \Delta f(E^{'})$`, proof done.

# hardness

some attempt

- for each element node, connect it to the target node `$x$`
- for each set, create dummy node `$d$` to connect to and connect `$d$` to all element nodes in the set
- also, compansating node by edges 

this will break for the example I sent to Lorenzo as well. 

- [ ] maybe we need other problems to reduce to?
- [ ] can it be solved optimally? using dynamic/integer programming?