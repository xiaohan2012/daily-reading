
for **custom object**, use [multiprocess.Manager](https://docs.python.org/2/library/multiprocessing.html\#managers) to create a proxy

- [related SO answer](https://stackoverflow.com/questions/28612412/how-can-i-share-a-class-between-processes)


also, [multiprocess.Value](https://docs.python.org/2/library/multiprocessing.html\#multiprocessing.Value)

seems to only work for `ctypes` (what are they?)