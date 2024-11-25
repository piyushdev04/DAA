Time Complexity: O(V+E)

Algorithm for BFS
Input:

Graph 

G(V,E) with V vertices and E edges, and a starting vertex.

Steps:

- Initialize a boolean array visited[] of size V to keep track of visited vertices.
- Create a queue and enqueue the starting vertex. Mark it as visited.
- While the queue is not empty:
  - Dequeue a vertex and visit it.
  - Enqueue all its unvisited adjacent vertices and mark them as visited.

Output:

BFS traversal order of the graph.