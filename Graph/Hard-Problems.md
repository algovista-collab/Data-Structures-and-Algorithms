## Reconstruct Itinerary
- https://leetcode.com/problems/reconstruct-itinerary/description/
- A Eulerian Path is a path that uses every edge exactly once.
- A Eulerian Circuit is a Eulerian Path that starts and ends at the same vertex.
- Hierholzer’s Algorithm (used for Eulerian paths)
- 

## Min Cost to Connect All Points
- https://leetcode.com/problems/min-cost-to-connect-all-points/description/

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

##
