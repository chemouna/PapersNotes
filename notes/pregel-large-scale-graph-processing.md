
## Pregel: A System for Large-Scale Graph Processing 

TLDR;

### Key Points 
- Graph algorithms often exhibit poor locality of memory access, very little work per vertex, and a changing degree of parallelism over the course of execution.
- Pregel computations consist of a sequence of iterations, called su- persteps. During a superstep the framework invokes a user- defined function for each vertex, conceptually in parallel.
- Values associated with the vertex and its edges are the only per-vertex state that persists across supersteps. Lim- iting the graph state managed by the framework to a single value per 
  vertex or edge simplifies the main computation cycle, graph distribution, and failure recovery.

- Sending a message, especially to a vertex on another machine, incurs some overhead. This can be reduced in some cases with help from the user. For example, suppose that Compute() receives 
  integer messages and that only the sum matters, as opposed to the individual values. In that case the system can combine several messages intended for a vertex V into a single message 
  containing their sum, reducing the number of messages that must be transmitted and bu↵ered 
  (For some algorithms, such as single-source shortest paths, we have observed more than a fourfold reduction in message traffic by using combiners.)

### Thoughts
