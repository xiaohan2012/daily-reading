# concepts

- computation grpah: graph where tensorflow operations are connected
- session: where computation graph runs
  - `session.run` to eval
- placeholder: a promise to provide a value later, like the training data
- variables: values that can be modified, like trainable parameter
  - `tf.assign`

# some modules

- `tf.train` to get different optimizers such as `tf.train.GradientDescentOptimizer`
- `tf.contrib.learn` provides higher level functions	
  - models  such as `LinearRegressor`
  - io functions such as `tf.contrib.learn.io.numpy_input_fn`
- you can define your own estimator using `tf.contrib.learn` 
  - the estimator returns `tf.contrib.learn.ModelFnOps`

# learned

## big picture

- define constants, placeholder, variables
- use operations to define loss
- use `tf.train` get the one optimization step to minimize loss (gradient update)
- `session.run` to evaluate

- `tf.contrib.learn`: estimator and IO util
- define custom estimator for `tf.contrib.learn` interfaces

## details

- use `tf.assign_add` to *update* the value
- `tf.group`: to group a set of operations like a Python `list`
- separating IO and model training/evaluation
  - `tf.contrib.learn.io`: needs to define the features and materialize them
  - estimator: needs to declare the features when initialized
