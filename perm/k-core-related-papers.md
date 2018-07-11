# engagement modeling 



Shaomei Wu, Atish Das Sarma, Alex Fabrikant, Silvio Lattanzi, Andrew Tomkins [Arrival and departure dynamics in social networks](https://dl.acm.org/citation.cfm?id=2433425), WSDM 2013
  - active users tend to belong to densifying cores
  - nodes at the fringe are more likely to depart

Fragkiskos D. Malliaros and Michalis Vazirgiannis [Vulnerability assessment in social networks under cascade-based node departures](http://iopscience.iop.org/article/10.1209/0295-5075/110/68006), EPL 2015
  - proposes *disengagement epidemic model*, related to k-core
  - can be used to run some simulation to test different network design algorithms

Fragkiskos D. Malliaros and Michalis Vazirgiannis [To stay or not to stay: modeling engagement dynamics in social graphs](https://dl.acm.org/citation.cfm?id=2505561), CIKM 2013
  - an earlier work using game theoy (related to the above paper)


# network design problems related to $`k`$-core

Rajesh Chitnis, Fedor V. Fomin and Petr A. Golovach [Preventing Unraveling in Social Networks Gets Harder](https://www.aaai.org/ocs/index.php/AAAI/AAAI13/paper/viewFile/6313/6872), AAAI 2013

Kshipra Bhawalkar, Jon Kleinberg, Kevin Lewi, Tim Roughgarden, and Aneesh Sharma [Preventing Unraveling in Social Networks: The Anchored $`k`$-Core Problem](https://epubs.siam.org/doi/abs/10.1137/14097032X), SIAM Journal on Discrete Mathematics 2015
- [slides](https://klewi.com/talks/kcore-icalp12.pdf)

Fan Zhang, Ying Zhang, Lu Qin, Wenjie Zhang, Xuemin Lin [Finding Critical Users for Social Network Engagement: The Collapsed k-Core Problem](https://www.aaai.org/ocs/index.php/AAAI/AAAI17/paper/download/14349/13769), AAAI 2017

Fan Zhang, Wenjie Zhang, Ying Zhang, Lu Qin and Xuemin Lin [OLAK: an efficient algorithm to prevent unraveling in social networks](http://www.vldb.org/pvldb/vol10/p649-zhang.pdf), VLDB 2017

Rajesh Chitnis and Nimrod Talmon [Can We Create Large k-Cores by Adding Few Edges?](https://link.springer.com/chapter/10.1007/978-3-319-90530-3_8), International Computer Science Symposium in Russia, 2018
  - problem: adding edges to have at least `p` nodes in `k` core, parametrized by edge budget `b`, core number `k` and goal `p`
  - when parametrized by `b+k+p`, it's `W[1]`-hard ([W hierarchy](https://en.wikipedia.org/wiki/Parameterized_complexity), concept in parameterized complexity)
  - proposes a dynamic programming algorithm which is [FPT (fixed parameter tractable)](https://stackoverflow.com/questions/19643939/what-is-fixed-parameter-tractability-why-is-it-useful)
  - no inapproximability result
  - [my note](july/anchored-k-core-adding-edge-edges.md)













