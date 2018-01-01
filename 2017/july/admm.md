# 

- [video by Boyd](https://www.youtube.com/watch?v=Xg0ozgCXXB8)
  - [slides](http://stanford.edu/~boyd/papers/pdf/admm_slides.pdf)
- [resources by Boyd](http://stanford.edu/~boyd/admm.html)

# goal

- scalablity: arbirary problem size
- decentralized: 
  - data too large to store in one machine
  - passing small amount of messages

basic idea:

decompose the objective function into simpler parts and do each part in parallel

coordination by dual variable update

- why use dual?
- why need **coordinate**? what if there is no coordinate?

# quesitons

- dual problem: intuition behind using this? dual decomposition
- why proximal operator
- how the composition is done in general?
