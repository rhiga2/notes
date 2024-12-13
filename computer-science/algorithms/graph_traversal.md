# Graph Traversal
## Terminology
* Graphs are represented as $(V, E)$ where $V$ is the vertex sert and $E$ is the edge set.
* Connected graphs: there exists a path between every pair of vertices.

## Traversal Framework
1. Select a start node and add the node to the bag and mark it.
2. Select node from bag
3. For each unmarked child, add child to bag and mark it. 
4. Repeat steps 2-3 until bag is empty

* Selecting node from bag can be implemented with the following ds:
  * Stack: Implements depth-first search
  * Queue: Implements breadth-first search
  * Priority queue on weighted edges: Implements Djikstra's algorithm
 
### Connectivity Check
* Undirected graphs: Call graph traversal starting at any node. If all nodes are marked, graph is connected.
* Directed graphs: Call graph traversal on the forward and reversed graph starting at any node. 
 
## Depth-First Search
### Recusive Approach 
* Alternative approach to implementing DFS
1. Call DFS on starting node and previsit starting node. 
2. Mark node
3. For each unmarked child, previsit and call DFS on child.
4. Postvisit node

### Cycle Detection
* If any child is already marked during previsit, then that indicates we have a cycle.
* A directed graph with no cycles is a directed acyclic graph (DAG).

### Topological Sort
* Topological sort: An ordering of nodes in a DAG such that parents occur before children.
* During postvisit add node to list and reverse the list to get topological sort. 

### Relationship Between Reverse Topological Sorting and Dynamic Programming 
* DP breaks up problem into subproblems using recursive relations. This forms a dependency graph.
* Directed edge $(v, w)$ indicates problem $v$ is dependent on subproblem $w$.
* DP solves dependencies (children) first. Thus it's equivalent to reverse topological traversal on a dependency graph.







