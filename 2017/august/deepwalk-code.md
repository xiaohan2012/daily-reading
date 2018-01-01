just checked the [code](https://github.com/phanein/deepwalk)

learned the following:

- parameters on walk: number of walks, length of each walk
  - window size to define context
- walk can be parallelized using `concurrent.futures`
  - `concurrent.futures` vs `multiprocessing`: simpler interface vs more flexibility
  - [more explanation](https://stackoverflow.com/questions/20776189/concurrent-futures-vs-multiprocessing-in-python-3)
- `wc -w` to count the words