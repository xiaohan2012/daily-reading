# Cultural Diffusion and Trends in Facebook Photographs

- extract topics from photos
- analyze patterns from these topics
  - temporal 
  - spatial: by country
  - role: friend, non-friend
- https://research.fb.com/wp-content/uploads/2017/08/15704-68517-1-pb.pdf

# Detecting Large Reshare Cascades in Social Networks

- reshare cascade detection: related to  event detection
  1. will it go viral
  2. how early can we predict it
- network agnostic
- https://research.fb.com/wp-content/uploads/2017/04/sansnet-www17.pdf

# Understanding Short-term Changes in Online Activity Sessions

- predict length of user's session and how much content the person will see.
- https://research.fb.com/wp-content/uploads/2017/04/www2017_kooti.pdf

# Automatic Alt-text Computer-generated Image Descriptions for Blind Users on a Social Network Service

- enhance photos with automatic generated caption
- with use study that reports better intrepretability
- https://research.fb.com/wp-content/uploads/2017/02/aat_cscw2017_camera_ready_20161031-2.pdf

# Discussion quality diffuses in the digital public square

- two different order methods for the comments in public Facebook pages
  - most recent
  - social feedback 
- found that social feedback produces higher "quality" comments (how to measure it?)
- https://research.fb.com/wp-content/uploads/2017/02/discussion-quality-diffuses-camera-ready.pdf

# Compressing Graphs and Indexes with Recursive Graph Bisection

- graph compression using graph ordering
- graph ordering: placing similar social actors nearby, useful for compression
- problem: finding the best compression-friendly ordering
- https://research.fb.com/wp-content/uploads/2016/11/compressing_graphs_and_indexes_with_recursive_graph_bisection.pdf

# Lost in Propagation? Unfolding News Cycles from the Source

- news cycle: the trace of information propagation
  1. comprehensiveness of news coverage on an event
  2. whether reaction and sentiment of news consumer diverge
- https://research.fb.com/wp-content/uploads/2016/11/lost_in_propagation_unfolding_news_cycles_from_the_source.pdf

# Changes in Engagement Before and After Posting to Facebook

- We find that after posting content people are more motivated to visit the site , are more attentive to content from friends (but not others), and choose to interact more with friends (in large part due to reciprocity)
- https://research.fb.com/wp-content/uploads/2016/11/changes-in-engagement-before-and-after-posting-to-facebook.pdf

# People and Cookies: Imperfect Treatment Assignment in Online Experiments

- challenge: identifying the same user across devices
- users may be partially treated/untreated (due to the identification chanllange)
- the paper study the effect of such problem
- https://research.fb.com/wp-content/uploads/2016/04/peopleandcookies.pdf

# Do Cascades Recur?

- define recurrence (elapsed time between bursts, overlap/proximity in social network, demographic diversity)
- explain the recurrence (initial virality is the driven factor)
- a model that predicts the recurrence
- https://research.fb.com/wp-content/uploads/2016/11/do_cascades_recur_.pdf

# Discovery of Topical Authorities in Instagram

- topical user discovery in instagram follower graph
  - applicable to user recommendation
- extract interests from self-reported biographies and applied label propagation
- Prehti's expert discovery on twitter?
- https://research.fb.com/wp-content/uploads/2016/11/discovery-of-topical-authorities-in-instagram.pdf

# Information Evolution in Social Networks

- meme mutates, how fast it mutates? and why it mutates?
- https://research.fb.com/wp-content/uploads/2016/11/information_evolution_in_social_networks.pdf

# Joint User-Entity Representation Learning for Event Recommendation in Social Network

- project user and event into the same latent space
  -  text CNN based
- https://research.fb.com/wp-content/uploads/2017/03/icde_2017_cameraready_609.pdf
# interesting directions

- event detection
- cascade inference (detect, predict)
- graph embedding
  - specific tasks: classification, recommendation
  - certain settings: temporal, large scale / distributed (cannot fit into main memory)
- machine learning in large scale networks (extreme multi-label classification, demographic inference)
- given the same topic/event, what are the reactions of people from different backgrounds
- how can we promote multi-cultural communication by recommending the "right" event?