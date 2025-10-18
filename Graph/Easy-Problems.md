## Number of Provinces or Number of Connected Components
- **Link:** https://leetcode.com/problems/number-of-provinces/description/
- https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/description/
- Two approaches: DFS and Union-Find
- DFS: TC - O(V+E), SC - O(V)
- Keep a visited array and loop over every row.  
- Increase count and call `dfs` function only if that row is not visited yet with `row`, `isConnected`, `visit`.  
- In the DFS function:  
  - Set `visit[row] = true` implying it’s visited.  
  - Loop over its neighbours.  
  - If any other node is connected and not visited yet, call the DFS for that node.
- Union-Find: TC - O(V+E), SC - O(V)
- Create 2 functions: `union` and `find`, implementing **path compression + union by rank**.  
- In the main function:  
  - Fill out the `root` and `rank` vector.  
  - Run a loop over every row and every column, and if they are connected, call `union` function.  
- Now `root` is updated with every index containing its root node as value.  
- union function will return 0 if they are already connected, else 1
- In the main function, counter -= union(u, v) decreases if union returns 1
- Number of Provinces has matrix which is n*n, hence TC - O(n²), SC - O(n)
  
## Graph Valid Tree
- https://leetcode.com/problems/graph-valid-tree/description/
- 
