## Reconstruct Itinerary
- https://leetcode.com/problems/reconstruct-itinerary/description/
- A Eulerian Path is a path that uses every edge exactly once, Hierholzer’s Algorithm (used for Eulerian paths)
- A Eulerian Circuit is a Eulerian Path that starts and ends at the same vertex.
- create unordered_map<string, priority_queue<string, vector<string>, greater<string>>> graph
- graph stores starting airport as key and destination airports in the priority_queue keeps the lexicographically smallest airport at the top
- run a for loop over tickets and push ticket[1] to the graph[ticket[0]] and call the dfs function with JFK, graph and result
- in the dfs function, run a while loop until the destination queue becomes empty and inside a loop call the dfs with top element
- once out of the loop, push the source airport to the result and in the main function reverse the result before returning

## Min Cost to Connect All Points (Kruskal's Algorithm)
- https://leetcode.com/problems/min-cost-to-connect-all-points/description/
- TC: O(N²*logN²) Time to remove all edges from Priority_queue is logE, SC: O(N²) (N is the number of points in the input array)
- Create a UnionFind class and in the main function create vector<pair<int, pair<int,int>>> all Edges
- run a for loop over n, currNode=0 and inner loop nextNode=currNode+1 and weights is the abs difference of x and y co-ordinates of curr and nextNode
- push the weight, currNode and nextNode to allEdges and after the loop sort the allEdges
- create an object of UnionFind and run a for loop until edgesUsed == n-1
- get the weight and nodes from allEdges and if the nodes are not already connected, add the weight to the totalCost and increment the edgesUsed

## Min Cost to Connect All Points (Prim's Algorithm): TC- O(N²), SC- O(N)
- https://leetcode.com/problems/min-cost-to-connect-all-points/description/
- vector<bool> inMst(n) and vector<int> minDist(n, INT_MAX) (initially distance between them are maximum)
- minDist[0] = 0 to start with this node and run a while loop until edgesUsed < n
- run a for loop over n nodes, if (!inMst[node] && currMinEdge > minDist[node]) then replace currMinEdge and currNode as node
- Once the node is added, make it true in inMst and edgesUsed++ and run a loop again over n to find the nextNode
- pick the node which is not in the MST yet and its minDist[nextNode] > weight, update the minDist[nextNode], finally return the mstCost

## Optimize Water Distribution in a Village
- https://leetcode.com/problems/optimize-water-distribution-in-a-village/description/
- TC: O(E*logE) SC: O(N)
- Create a UnionFind class with find and join methods implemented
- In the main function, create vector<vector<int>> edges to store the cost, house1, house2
- first loop creates a virtual house to show the cost of wells built in each house, push {wells[i], 0, i+1}
- second loop goes through the pipes to store the cost and the houses
- sort edges and create an object of the class UnionFind uf(n+1)
- loop over the edges and check if the house are already connected by calling join method
- if not connected yet, add their cost to the total cost and return the total cost in the end
