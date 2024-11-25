Time Complexity: O(V^2)

Algorithm for Prim's MST
Input:

A weighted graph 
G(V,E) with vertices V and edges E.

Steps:

- Initialize key[] to +∞ and mstSet[] to false.
- Set key[0] = 0 (start with the first vertex) and parent[0] = -1.
- Repeat until all vertices are included in MST:
  - Pick the vertex u with the smallest key value that is not in mstSet.
  - Include u in mstSet.
  - Update key[] and parent[] for all adjacent vertices of u:
       - If graph[u][v] < key[v] and v is not in mstSet, set parent[v] = u and key[v] = graph[u][v].

Output:

The edges and weights in the MST.