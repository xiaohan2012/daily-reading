# introduction

papers on k-core decomposition on dynamic graphs

# centralized

1. Rong-Hua Li and Jeffrey Xu Yu, **Efficient core maintenance in large dynamic graphs**, IEEE Trans. Knowl. Data Eng., 2014.

2. [X] A. E. Saruce, B. Gedik, G. Jacques-Silva, K.-L. Wu,ıyand U. V. ¸
Catalyurek. **Streaming algorithms for k-core decomposition**. PVLDB, 6(6):433–444, Apr. 2013.

considers inserting/deleting an edge

main theorems:

1. core number is change at most 1 (theorem 1)
2. upper end point will not change core number (theorem 2)
3. nodes whose core number might change form a connected component where nodes inside core number equal to `K(u)` (theorem 3)

proposed three algorithms for insertion:

1. subcore: use notion of sub core to locate the candidates (simpliest)
2. pure core: use notion of maximal core degree, MCD (better)
3. TRAVERSAL: use pure core degree (best)

deletion is based on MCD

3. D. Miorandi and F. De Pellegrini. **K-shell decomposition for dynamic complex networks**. In Proc. of the 8th Int. Symposium on Modeling and Optimization in Mobile, Ad Hoc and Wireless Networks), WiOpt’10, 2010.

4. J. Cheng, Y. Ke, S. Chu, and M. T. Ozsu. **Efficient core decomposition in massive networks**. In Proc. of the 27th Int. Conf. on Data Engineering, ICDE ’11, pages 51–62, Washington, DC, USA, 2011. IEEE Computer Society.

5. Zhang, Y., Yu, J. X., Zhang, Y., & Qin, L. (2016). **A Fast Order-Based Approach for Core Maintenance**. Retrieved from https://arxiv.org/pdf/1606.00200.pdf

7. D. Wen, L. Qin, Y. Zhang, X. Lin, and J. X. Yu. **I/O efficient core graph decomposition at web scale**. In Proc. of ICDE’16, 2016. 
   - semi-external algorithm


# parallel/distributed

1. H. Aksu, M. Canim, Y.-C. Chang, I. Korpeoglu, and O. Ulusoy. 
**Distributed k -core view materialization and maintenance for large dynamic graphs**. IEEE Trans. Knowl. Data Eng., 26(10):2439–2452, 2014. (for fixed k value)

2. P. Jakma, M. Orczyk, C. S. Perkins, and M. Fayed. **Distributed k-core decomposition of dynamic graphs**. In Proc. of the 2012 ACM CoNEXT Student Workshop, New York, NY, USA, 2012. ACM. (can be ignored)

3. [X] Sabeur Aridhi, Martin Brugnara, Alberto Montresor, Yannis Velegrakis, **Distributed k–core Decomposition and Maintenance in Large Dynamic Graphs**, DEBS, 2016

4. [X] Wang, N., Yu, D., Jin, H., Hua, Q.-S., Shi, X., & Xie, X. (n.d.). **Core Maintenance in Dynamic Graphs: A Parallel Approach based on Matching**. Retrieved from https://arxiv.org/pdf/1703.03900.pdf

main theorem: if the inserted/deleted edges form a matching (edges that do not share common endpoints), the core number change is at most 1.

main algorithm: 

- split the edges into matchings
- for each matching, insert the edges in parallel
- further, edges whose lower end point are in the same core can be processed in batch to reduce duplicate vertex visiting
  - **comment**: it has some treatment with batch processing
  - the algorithm is directly related to *[Saruce, 2013]*

- comapred with TRAVERSAL in *[Saruce, 2013]*, speedup ratio ~100
- on single machine





