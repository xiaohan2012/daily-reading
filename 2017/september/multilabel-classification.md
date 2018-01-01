# overview

mainly two families:

- embedding-based
- tree-ensemble

addressing label dependency is a topic

# embedding-based

main idea:

- compression: project label space (dim $`L`$) into lower dimension one (dim $`\hat{L}`$), where $`\hat{L} \ll L`$
- then prediction is made on $`\hat{L}`$? 
- decompression: project back from lower-dim label space back to $`L`$

compression and decompression differs

- advantages: optimization method known, nice theoretical grounding
- disadvantageds: decompressing losses information

# tree-ensemble

learn an ensemble of decision trees

- each decision tree uses a random subset of features
- each node focus on predicing a small subset of labels

each node is split by learning a hyperplane (weighted combination of all features)

- instead of a single feature in traditional decision tree training 
- learn based on what? how is the learning done?

advantage: prediction is logarithmic if tree is balanced 
