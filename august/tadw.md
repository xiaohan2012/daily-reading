# idea

![illustration](https://ibin.co/3WP23iEkxulU.png)

proved deepwalk can be viewed a matrix factorization problem

now how to add text and still model it as a MF problem?

- take one of the two factor matrices
- factor it further into a feature matrix and another smaller matrix
  - this actualy give us two representations for each node
  - this paper concatenate them into length `2k` vector

benefits:

- a way to incorporate text features
- reduces parameter size as well

# leared

- deepwalk using to sets of representations and latter concatenate them
- a way to incorporate features into MF model
- [imagebin](https://imagebin.ca/) is cool