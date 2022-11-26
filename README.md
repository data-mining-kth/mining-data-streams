# Mining Data Streams with TRIEST algorithm

## Reflection

1. **What were the challenges you have faced when implementing the algorithm?** 

Overall, the paper described a good implementation in pseudocode of the algorithm so it was easy to follow the logical steps and implement them in Python. Nevertheless, understanding the relation of edges and their relative increment or decrement in the counters wasn't immediate.

2. **Can the algorithm be easily parallelized? If yes, how? If not, why?**

As the algorithms takes edges as they arrive from the stream, one by one, it can't be parallelized. Instead, what can be parallelized is the update of counters.

3. **Does the algorithm work for unbounded graph streams?**

The algorithm can also operate on unbounded data streams. The algorithm simply requires the current triangles counter, the size of the sample S, and the number of observed samples in the stream.

4. **Does the algorithm support edge deletions? If not, what modification would it need?**

The two versions TRIÈST-BASE and TRIÈST-IMPR do not support edge deletions, while TRIÈST-FD does support a fully-dynamic version of streams. 
To do so, TRIÈST-FD leverages the concept of Random Pairing (RP). By keeping track of the number of edges deleted from the sampleset and the overall number of deletions, it drives the insertion of a new edge in the sampleset and returns the estimation of the number of triangles with a new formula.
