# Automatic controversy detection in social media: A content-independent motif-based approach

https://www.sciencedirect.com/science/article/pii/S2468696417300721

# related work

Kiran's WSDM 2016 paper, assumptions:

1. the conversaion graph partitions into 2 clusters
2. clear partitioning of the conversation graph indicates disccusion over controversial topics
   - might not hold if one tag is just used in two communities
   - also non-controversial hashtag might contain controversial sub-conversation

essentially unsupervised

# approach

- supervised machine leaning based on network *motifs*
- avoid text analysis so language independent

further assumption

- one controversial event corresponds to one hashtag

# learned

- some weakness/strong assumption of Kiran's WSDM paper
- using motif as feature for a supervised classifier
