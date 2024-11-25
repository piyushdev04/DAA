Algorithm for Kruskal's MST
Input:

A weighted graph 

G(V,E) with vertices V and edges E.

Steps:

- Sort all edges in ascending order of their weight.
- Initialize subsets for union-find.
- Iterate over sorted edges:
  - If the edge connects two different subsets, add it to the MST and union the subsets.
- Stop when V−1 edges are included in the MST.

Output:

The edges and weights in the MST.