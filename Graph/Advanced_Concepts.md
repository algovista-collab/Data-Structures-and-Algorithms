## Kruskal's Algorithm
- Ascending sort all edges by their weight
- Add edges in that order into the MST, skip the edges that would produce cycles in the MST
- Repeat step 2 until N-1 edges are added
- This is same as greedy algorithm as greedy also add edges with the least weight and not creating any cycle
- TC: O(E.logE) (E: number of edges and we sort them), we need O(E alpha(E)) to form the edge by checking if the vertices belong to the same component
- SC: O(V) (We use root array to store all the vertices)

## Prim's Algorithm
- Either we use Binary min-heap (TC: O(E * logV)) or Fibonacci heap (TC: O(E + V logv))
- Binary heap takes O(V+E) time to traverse all the vertices of the graph. Extract the minimum element and ey decreasing operations cost O(logV) time
- Fibonacci heap extracts the minimum elements that takes O(logV) time while key decreasing operation will take amortized O(1) time. SC: O(V)
- This expands the MST by adding vertices whereas Kruskals expands by adding edges
