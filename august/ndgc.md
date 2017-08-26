# task

given query $`q`$, and returned ranked list of documents, $`d_, \ldots, d_p`$

# Cumulative gain

$`\mathrm{CG_{p}} = \sum_{i=1}^{p} rel_{i}`$

- ranking order does not matter
- just summing up relevance scores of top-p ranked documents

# Discounted Cumulative Gain

$`\mathrm{DCG_{p}} = \sum_{i=1}^{p} \frac{rel_{i}}{\log_{2}(i+1)} = rel_1 + \sum_{i=2}^{p} \frac{rel_{i}}{\log_{2}(i+1)}`$

- add a damping factor $`\log_{2}(i)`$ so that highly ranked documents gets smaller damping. 
- order now matters

$`\log`$ is added to smooth the score. some theoretical justification is made. 

## alternative formulation

places more emphasis on highly relevant documents. 

$`\mathrm{DCG_{p}} = \sum_{i=1}^{p} \frac{ 2^{rel_{i}} - 1 }{ \log_{2}(i+1)}`$

# normalized Discounted Cumulative Gain (nDCG)

normalize by $`IDCG_{p}`$, the DCG score of ground-truth ranking:

$`\mathrm{nDCG_{p}} = \frac{DCG_{p}}{IDCG_{p}} `$

where:

$`\mathrm{IDCG_{p}} = \sum_{i=1}^{|REL|} \frac{ 2^{rel_{i}} - 1 }{ \log_{2}(i+1)} `$


