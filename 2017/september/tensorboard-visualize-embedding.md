documentation: https://www.tensorflow.org/versions/r0.12/how_tos/embedding_viz/

- [how to use t-SNE effectively](https://distill.pub/2016/misread-tsne/)
- [example for cifar](https://github.com/oduerr/dl_tutorial/blob/master/tensorflow/debugging/embedding.ipynb)

# learned

- when launching tensorboard, make sure `--logdir` points to the checkpoint directory

- to show by category color, create a column with integers representing the labels in the `tsv` file

- `du -hs * | sort -h`: sort by size

# update (dec-14, 2017)

the main idea:

- save the variable into the checkpoint
- set `embedding.tensor_name`
- set `embedding.metadata_path`