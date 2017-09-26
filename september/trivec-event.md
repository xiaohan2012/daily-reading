# TrioVecEvent: Embedding-Based Online Local Event Detection
in Geo-Tagged Tweet Streams

goal: detecting events from geo-tagged tweet streams

challenges

1. short text semantics: *vs* keyword based approach
2. filtering uninterested activities: *vs* top-k approaches
   - k is fixed thus inappropriate for cases where are more than k interesting events or fewer than k interesting events
3. fast online detection: report as soon as possible


# approaches

1. learning embeddings for regions, hours and text
   - based on CBOW

2. cluster online clustering of tweets into the geo-topic clusters (each cluster as an event candidate)
   - bayesian mixture model

3. candidate classification based on extracted features (compared to top-k approach)
   - there are some labeled dataset


http://www.kdd.org/kdd2017/papers/view/triovecevent-embedding-based-online-local-event-detection-in-geo-tagged-twe