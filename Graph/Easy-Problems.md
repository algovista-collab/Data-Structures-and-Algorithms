## Number of Provinces or Number of Connected Components
- https://leetcode.com/problems/number-of-provinces/description/
- https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/description/
- Two approaches: DFS and Union-Find
- DFS: TC - O(V+E), SC - O(V)
- Build a adjList and keep a visited array and loop over every vertex.  
- Increase count and call `dfs` function only if that vertex is not visited yet with `vertex`, `adjList`, `visited`.  
- In the DFS function(vector<int> adjList[], vertex, visited):  
  - Set `visit[vertex] = 1` implying it’s visited.  
  - Loop over its neighbours => i=0 to adjList[vertex].size().  
  - If any other node is connected and not visited yet, call the DFS for that node (adjList[vertex][i]).
- Union-Find: TC - O(V+E), SC - O(V)
- Create 2 functions: `union` and `find`, implementing **path compression + union by rank**.  
- In the main function:  
  - Fill out the `root` and `rank` vector.  
  - Run a loop over every row and every column, and if they are connected, call `union` function.  
- Now `root` is updated with every index containing its root node as value.  
- union function will return 0 if they are already connected, else 1
- In the main function, counter -= union(u, v) decreases if union returns 1
- Number of Provinces has matrix which is n*n, hence TC - O(n²), SC - O(n)
  
## Graph Valid Tree: TC - O(N⋅α(N)), SC - O(N)
- https://leetcode.com/problems/graph-valid-tree/description/
- If edges.size() != n-1, then return false. Because if less than n-1 it is disconnected, if more than n-1 it has cycle
- Construct the root, rank vector. Create find(), unionSet(), connected() functions
- Loop over the edges, if nodes are connected return false - it contains cycle
- If not connected, then call unionSet() to make a connection

## Find if Path Exists: TC - O(V+E), SC - O(V+E)
- https://leetcode.com/problems/find-if-path-exists-in-graph/description/
- Can be solved disjoint set data structure which is easier or dfs as below
- Keep an unordered_map to store all the edges and visited unordered_set to store visited vertices
- Loop over all the edges connected to source and go to their corresponding edges in the dfs function
- dfs function: if vertex is already destination return true
- insert the vertex to visited and loop over its edges, if not visited yet call the dfs again
- if destination is not found at all, return false

## All paths from source to target: (Yet to understand time and space complexity)
- https://leetcode.com/problems/all-paths-from-source-to-target/description/
- keep a path and result, call dfs function with source, target, path, result, graph
- add the source to path and if source == destination, add path to the result
- else, run a loop over graph[node] and call dfs on its neighbour
- in the end, path.pop_back()

## Clone Graph: TC - O(N+M), SC - O(N)
- https://leetcode.com/problems/clone-graph/description/
- unordered_map<Node*, Node*> visited which has key as original node and value as its cloned node
- dfs function returns visited[node] if already exits or node if null
- Else create a new Node(node->val) and run a for loop over its neighbours and call dfs function over its neighbour node
- Once dfs returns newNode, push_back the newNode to cloned node neighbour vector
