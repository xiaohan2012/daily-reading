# goal

tag stackexchange posts

# different ways to predict tags

## heterogenous nework

- full network involving user, post, comment, tag
- embedding for user, post
  
the question is, should tag have embedding?

- **yes**: unsupervised learning
  - like representation learning with network regularization
  - like the author identification paper, hinge loss
  - additional benefits:
    - tag user
    - visualize tags
- **no**: semi-supervised learning
  - representation of post feed into some `FC+softmax` layer
  - no embedding for tag, so no intersting "by-products"

## homogeneous network

- network of posts, where some posts are tagged
- posts are connected by the common user the shared
  - weights need to be designed somehow
- then, a semi-supervised problem
  - "revisit" papper applies here

## absense of network

- consists of (text, tags) pairs. 
- a classific supervised learning problem

# semi-supervised learning

two sets of embeddings:

- post
- user

to predict tag, concatenate embeddings of post and users:

- for post (question + answer), there is only one vector
- for users, there might have  multiple ones, take the average


# unsupervised learning

three sets of embeddings:

- post
- user
- tag

to predict the tag, use joint embeddings of post and users

   - because we need to enhance embedding merely from post

how to design the function? `d(w_t, f(w_p, w_u))`

- `f` "organizes" `w_p` and `w_u` into length-`k` vector, for example:
  - take average
  - concat and then linear mapping

- `d` can:
  - hinge loss (difference to negative sampling?)
  - binary logistic regression?

## easier approach

equivalent role of user/post/tag. so:

- user predicts tag? 
- post predics tag? 

however, if  tag predicts user? 
  - hard. too many users may be associated with one tag
  - negative sampling can be a positive user

**BP**

# auto-encoder for heterogenous network

?

# proximity definition

meta-path guided random walk

- what meta path to use?
- ratio of each path?