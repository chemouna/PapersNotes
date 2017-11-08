
## Pregel: A System for Large-Scale Graph Processing 

TLDR; Pregel is a programming model specifically targeted to large-scale graph problems, Pregel's programming model fundamentally uses message passing between vertices in a graph. 
Pregel organizes this message passing into a sequence of iterations called supersteps. At the beginning of each superstep, the framework runs a user-specified compute function on 
each vertex, passing it all the messages sent to that vertex during the last superstep. The compute function has the opportunity to process these messages and then send messages 
to other vertices, which will be received in the next superstep. It also can "vote to halt," deactivating the vertex it's running on until the vertex receives a message. 
Once all vertices have voted to halt, the job terminates.

### Key Points 
- Graph algorithms often exhibit poor locality of memory access, very little work per vertex, and a changing degree of parallelism over the course of execution.
- Pregel computations consist of a sequence of iterations, called su- persteps. During a superstep the framework invokes a user- defined function for each vertex, conceptually in parallel.
- Values associated with the vertex and its edges are the only per-vertex state that persists across supersteps. Lim- iting the graph state managed by the framework to a single value per 
  vertex or edge simplifies the main computation cycle, graph distribution, and failure recovery.

- Sending a message, especially to a vertex on another machine, incurs some overhead. This can be reduced in some cases with help from the user. For example, suppose that Compute() receives 
  integer messages and that only the sum matters, as opposed to the individual values. In that case the system can combine several messages intended for a vertex V into a single message 
  containing their sum, reducing the number of messages that must be transmitted and bu↵ered 
  (For some algorithms, such as single-source shortest paths, we have observed more than a fourfold reduction in message traffic by using combiners.)

- Pregel aggregators are a mechanism for global communica- tion, monitoring, and data. Each vertex can provide a value to an aggregator in superstep S, the system combines those values 
  using a reduction operator, and the resulting value is made available to all vertices in superstep S + 1.
  
- The assignment of vertices to worker machines is the main place where distribution is not transparent in Pregel. Some applications work well with the default assignment, but some benefit 
  from defining custom assignment functions to better exploit locality inherent in the graph. 


### Thoughts
