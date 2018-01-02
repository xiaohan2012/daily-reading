# NeuPL: Attention-based Semantic Matching and Pair-Linking for Entity Disambiguation

highlights:

- entity diambiguiation by learning embedding using LSTM and attension mechanism (word and mention ordering is considered)
  - local perspetive
- collecting linking via resolving pairs of mentions at a time
  - global perspective (coherence)


assumption:

- mentions are extracted
- each mention are linkable (no not-in-list problem)
 
# candidate generation

1. build dictionary using entity name / anchor text, redirect pages, etc
2. if mention has no dictonary item, use n-grams to retrieve candidates (for higher recall)
3. mention bounary correction using Named Entity Recognizer

train Gradient Boosted Tree for candidate ranking using the following statistical features 

- prior probability
- textual similarities: edit distance, etc


# word and entity embedding

jointly training word and entity embedding using word2vec

in addition to the original sentence:

- in each page, each mention is replaced by its associted entity id
- for each page, extract the mentions and create a sentence with the entity ids in order

how about the entity and its page?

# LSTM

to learn representaton for mention context and entity description

- input: embeddings of word sequence
- output: one vector after max-pooling over all output hidden states

