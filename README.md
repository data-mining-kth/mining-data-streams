Mining Data Streams

## Questions

1. What were the challenges you have faced when implementing the algorithm?
The algorithm was well documented, even comprising pseudocode, so the most challenging part involved choosing the most suitable data structures. In particular, the choice of the data structure for the sampleset is documented in the solution section.

2. Can the algorithm be easily parallelized? If yes, how? If not, why? Explain.
Introducing data parallelism in the algorithm does not make sense since it is designed for a stream, and the operations on the counters are blocking. Moreover, the operations on the counters rely on the current state of the sampleset, which can be modified dynamically. However, some level of task parallelism can be introduced. In particular, computing the sets of nodes one hop away from the considered node might be parallelized.

3. Does the algorithm work for unbounded graph streams? Explain.
The algorithm works on unbounded data streams and can be queried at any time for the current estimation of the number of triangles. As visible in the experiments, the algorithm needs only the current triangles counter, the size of the sampleset and the number of observed samples in the stream to work.

4. Does the algorithm support edge deletions? If not, what modification would it need? Explain.
Although TRIÈST-BASE and TRIÈST-IMPR do not support edge deletions, the same paper where they are presented describes TRIÈST-FD, a fully dynamic version. TRIÈST-FD builds upon the concept of Random Pairing (RP) by keeping track of the number of edges deleted from the sampleset due to deletion in the stream and the overall number of deletions. This information then drives the insertion of a new edge in the sampleset and the formula for the estimation of the number of triangles.
