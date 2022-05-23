# Graphs

A graph is a non-linear data structure that can be looked at as a collection of vertices (or nodes) potentially connected by line segments named edges

common terminology 
1. Vertex - “node”
2. Edge -  is a connection between two nodes.
3. Neighbor - its adjacent nodes
4. Degree -  is the number of edges    connected to that vertex.

`Undirected Graph` : is a graph where each edge is undirected or bi-directional
`Directed Graph` :  is a graph where every edge is directed.

##  types of graphs

1. Complete Graphs
2. Connected :have at least one edge.
3. Disconnected : some vertices may not have edges.
4. Acyclic Graph
5. Cyclic Graphs :graph that has cycles

*Adjacency Matrix*

* a sparse graph is when there are very few connections. a dense graph is when there are many connections

*Adjacency List*

An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected.

6. Weighted Graphs : graph with numbers assigned to its edges

 **what the algorithm breadth first traversal looks like:**

  1. Enqueue the declared start node into the Queue.
  Create a loop that will run while the  node still has nodes present.
  2. Dequeue the first node from the queue
  3. if the Dequeue‘d node has unvisited  child nodes, add the unvisited children  to visited set and insert them into the  queue.

    ```
    ALGORITHM BreadthFirst(vertex)
        DECLARE nodes <-- new List()
        DECLARE breadth <-- new Queue()
        DECLARE visited <-- new Set()
        breadth.Enqueue(vertex)
        visited.Add(vertex)
        while (breadth is not empty)
            DECLARE front <-- breadth.Dequeue()
            nodes.Add(front)
            for each child in front.Children
                if(child is not visited)
                    visited.Add(child)
                    breadth.Enqueue(child)   
    
        return nodes;
    
    ```

   **The algorithm for a depth first traversal**
  1. Push the root node into the stack
  2. Start a while loop while the stack is not  empty
  3. Peek at the top node in the stack
  4. If the top node has unvisited children,  mark the top node as visited, and then Push  any unvisited children back into the stack.
  5. If the top node does not have any unvisited  children, Pop that node off the stack
  6. repeat until the stack is empty


 **Real World Uses of Graphs**

    1. GPS and Mapping
    2. Driving Directions
    3. Social Networks
    4. Airline Traffic
    5. products



