# mapreduce basic

split-apply-combine paradim

- map/apply: map each input record to (key, value) pair
- reduce/combine: group the pairs by key, `(key, val1, val2, val3, ...)` and combine the values

combine can be: filter, sum, average, count, max, min, etc

# examples

## word count

- map: `(word, freq)`, and `freq=1`
- combine: for `(key, val1, val2, val3, ...)`, add up `val1`, `val2`, `val3`...

## max/min value

- map: `(1, val)`, no key is needed here
- combine: take the max/min of `val1`, `val2`, `val3`

## inverted index

input: list of documents
output: inverted index like `{word1: [doc1, doc2, ...], word2: [doci, docj, ..]}`

- map: tokenize document, emit records `(word, doc)`
- reduce: `(word, doc1, doc2, ..)`, group the docs `(word, [doc1, doc2, ...])`	

## term frequency

- map: tokenize document, emit records `(word, 1)` if word exist in the document
- reduce: just like word count, `(word, c1, c2, c2, ...)`, add up `c1, c2, c3, ...`

# reference

- https://www.tutorialspoint.com/map_reduce/map_reduce_tutorial.pdf