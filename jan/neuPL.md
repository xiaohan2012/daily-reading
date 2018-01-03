# NeuPL: Attention-based Semantic Matching and Pair-Linking for Entity Disambiguation

## highlights:

- entity diambiguiation by learning embedding using LSTM and *attention* mechanism (word and mention ordering is considered)
  - local perspetive
- collecting linking via resolving pairs of mentions at a time
  - global perspective (coherence)
  - **speed**


## assumption:

- mentions are extracted
- each mention are linkable (no not-in-list problem)
 
## components

- candidate generation (generation, ranking)
- embedding learning and similarity learning (LSTM + attention)
- collective linking (pair-linking, early-stopping)

# candidate generation

two steps:

- coarser candidate generation 
- candidate ranking 
- return the top-`k` as candidates

1. build dictionary using entity name / anchor text, redirect pages, etc
2. if mention has no dictonary item, use n-grams to retrieve candidates (for higher recall)
3. mention bounary correction using Named Entity Recognizer

train Gradient Boosted Tree for *candidate ranking* using the following statistical features 

- prior probability
- textual similarities: edit distance, etc

and take the top-k candidates. 



# word and entity embedding

jointly training word and entity embedding using word2vec

in addition to the original sentence:

- in each page, each mention is replaced by its associted entity id
- for each page, extract the mentions and create a sentence with the entity ids in order

how about the entity and its page?

# similarity between mention context and entity

## context representation

to learn representaton for mention context 

- input: embeddings of word sequence
- output: one vector after max-pooling over all output hidden states

more details:

- two LSTMs to model the left and right context of the mention
- aware of the position of the mention (that's why there are two LSTMs)


## entity representation

one LSTM for the entity description (first k words) concatenated with entity representation (learned using word2vec)

## attention mechanism

motivation: highlight the more informative parts of the inputs to the given attention vector

- inputs: one attention vector (the entity vector) and another vector to be reweighted
- output: the reweighted vector

## output layer

multi-layer perception with:

- input: concatenation of the context representation and entity representation
- output: similarity score



# pair-linking

input: `n` mentions and a set of candidate entities for each mention

1. for each pair of mentions, pick the *top* entity pair (score by matching scores between (entity, mention) and coherence between the entity pair)
2. for all the pairs, pick the most confident pair, fix the assignment, reassign the top entity pair and re-run this line until all (mention, entity) are fixed. 

for line 1, naively, it's `O(n^2)`.

*early stopping* is applied: for each mention, sort the candidate entities by relatedness. scan them in descending order and stop if the score is worse than the highest score by a specific margin. 



comment: a local verion of (mention, entity) assignment

