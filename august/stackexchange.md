for most sites:

- num. questions : num. answers : num. comments = 1:1:4
- tags ~ or < 1k
  - many questions do not have tags
  - so our problem can be supervised or semi-supervised problem


# data tables

- `Posts`: both question and answer
  - answer has `ParentId`
- `Comments`: we should use this
- `User`
- `Votes`: if `TypeId=5`, it means favourite
  - upvote and downvote are anonymous

# links

- [datascience query](https://data.stackexchange.com/datascience/)
- [site list](https://data.stackexchange.com/)

# question

- how can we use user-user, user-post, user-comment relationships to enchance post classification result? 