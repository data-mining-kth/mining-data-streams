Mining Data Streams

## Questions

1. What were the challenges you have faced when implementing the algorithm?
Overall, the paper described a good implementation in pseudocode of the algorithm so was easy to follow the logical steps and implement them in python. Nevertheless, understanding the relation of edges and their relative increment or decrement in the counters was a bit tricky.

2. Can the algorithm be easily parallelized? If yes, how? If not, why? Explain.
As the algorithms takes the edges as they arrive in a stream, one by one, this can't be parallelized.
What can be parallelized is the update of counters.

3. Does the algorithm work for unbounded graph streams? Explain.
The algorithm can also operate on unbounded data streams. The algorithm simply requires the current triangles counter, the size of the sample S, and the number of observed samples in the stream.

4. Does the algorithm support edge deletions? If not, what modification would it need? Explain.
The two versions TRIÈST-BASE and TRIÈST-IMPR do not support edge deletions, TRIÈST-FD, instead, does support a fully dynamic version. 
TRIÈST-FD leverages the concept of Random Pairing (RP) by keeping track of the number of edges deleted from the sampleset due to deletions in the stream and the overall number of deletions. This information then drives the insertion of a new edge in the sampleset and the formula for the estimation of the number of triangles.
