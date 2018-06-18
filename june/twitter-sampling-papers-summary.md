# [How Does the Data Sampling Strategy Impact the Discovery of Information Diffusion in Social Media, ICWSM, 2010](http://www.contrib.andrew.cmu.edu/~aislingk/papers/dechoudhury_ICWSM10.pdf)

question: "accuracy" of tweet sampling strategies, where "accuracy" is defined by the similiarty between some estimated diffusion statistics and the real stat.
- note that this requires *ground-truth graph* to compare against

two steps:

1. use some sampling technique to extract subgraph
   - random
   - based on location
   - based on graph topology
   - etc
2. subgraphs are used to estimate some diffusion statistics
   - reach: tree depth
   - spread: tree width
   - volume: ratio of detected active users
   - etc

in experiment, the ground-truth graph is obtained via crawling (also sampling) as well, which might create bias

# [Is the Sample Good Enough? Comparing Data from Twitter’s Streaming API with Twitter’s Firehose](https://www.aaai.org/ocs/index.php/ICWSM/ICWSM13/paper/download/6071/6379)

Dimensions to compare between sampled version and firehose version:

- hashtag
- topic
- induced network
- geographical location

note on experiment:


- focused on a given set of keywords, geolocation box, etc
- compares against *uniform sampling*
- to find *popular* hashtags, streaming API may not be good to use. but for infrequent hashtags, it's appropriate.
  - for random sampling approach, the result is opposite
- for topic modeling, random sampling gives better result than streaming
- network stat: to be cont'd

# [When is it Biased? Assessing the Representativeness of Twitter’s Streaming API](https://arxiv.org/pdf/1401.7909.pdf)

problem: finding  sample  bias  without  the  need  for “gold standard” Firehose  data



# side note:

to be fair, sampling should balance:

- location
- age
- profession
- gender