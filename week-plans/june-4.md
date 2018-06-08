- [X] illustraion on lattice: our/netfill/pagerank  
- node recovery
  - [X] by cascade size
  - [X] by observation fraction
- edge recovery
  - [X] by cascade size
  - [X] by observation fraction
- real cascade
  - [X] by observation

- graph statistics table

# parabel

understand:

- running the code:
  - [X] run it on some small dataset
- understand the code
  - [ ] read the paper again
  - [ ] map the parameters in the code to the paper
  - [X] map the functions in the code to the paper
  - [X] find out where the partitioning happens
- understand the metis code
  - [code](http://glaros.dtc.umn.edu/gkhome/metis/metis/download)
  - [doc](http://glaros.dtc.umn.edu/gkhome/fetch/sw/metis/manual.pdf)
    - page 26
  - [example of using metis in C++](https://gist.github.com/erikzenker/c4dc42c8d5a8c1cd3e5a)

- [X] label graph construction
- [ ] dump to file and read by metis in C++
- [ ] recurive partition in C++, replace the `balanced_kmeans` function