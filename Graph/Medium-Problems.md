## Smallest String With Swaps
- https://leetcode.com/problems/smallest-string-with-swaps/description/
- TC - O((V+E)alpha(V) + V logV) [V-length of the string], SC - O(V)
- Build the root and rank using DSU functions
- Create an unordered_map with int as key and vector<int> as values
- Loop over length of string and find the root of every index and make it a key and push the index as values
- Every element in the map are connected and can be swapped - we need to sort them
- Loop over the map, collect the characters corresponding to the indices in the map and sort them and store them in the result string based on their index

## Evaluate Division (Study later - union find solution)
- https://leetcode.com/problems/evaluate-division/description/
- TC - O(M.N), SC - O(N); M - number of queries, N - number of input equations
- Data structure: unordered_map<string, unordered_map<string, double>> to store numerator - (denominator, value)
- Run a loop over queries: if graph doesn't contain push -1.0 to the result, if both numerator and denominator are same push 1.0
- Else call dfs function with numerator, denominator, visited (unordered_set) to store visited string, 1.0
- dfs function will insert numerator to the visited, if graph[numerator] has the denominator - return the value
- Else, check if there is a path between them by loop over the map of the numerator, skip if already exists in visited
- call dfs recursively and if found erase the string from visited and return result, if not found return -1.0

## All Paths from Source lead to Destination: TC - O(V+E), SC - O(V)
- https://leetcode.com/problems/all-paths-from-source-lead-to-destination/description/
- We use unordered_map<int, vector<int>> to store the vertices and their outgoing edges
- We use vector<int> visited(n,0) to store all the nodes from 0 to n-1 and initialize them to 0 meaning not yet visited
- dfs function returns false if visited[node] is 1, which means cycle exists and returns false if node has no outgoing edge but not a destination
- returns true if node state is 2, i.e. already visited and the path leads to destination
- if none of the above, set the state as 1 and run a for loop over its edges and call dfs recursively
- if dfs returns false, immediately returns false else set the state as 2 and return true

## Shortest Path in Binary Matrix: TC - O(N), SC - O(N)
- N is the number of cells in the matrix
- https://leetcode.com/problems/shortest-path-in-binary-matrix/description/
- queue<pair<int,int>>, vector<vector<int>> dirs = {{-1,-1}, {-1,0}, {0,-1}, {1,1}, {1,0}, {0,1}, {1,-1}, {-1,1}};
- start with 0,0 and go in all directions
- run a loop until q is empty, increment result and push the 8 adjacent cells only if the grid has 0 in them, mark them visited
- return the result if x and y is the last cell else return -1 when the loop ends

## Rotten Oranges: TC - O(n*m), SC - O(n*m)
- https://leetcode.com/problems/rotting-oranges/description/
- we store all row,col pair which have 2 as their value in the queue to count the time from them and increment fresh for cells which have 1 as their value
- if fresh is 0 (no good oranges) return 0 else run a loop until q is empty and main a vector of 4 directions
- run a for loop inside for the size of the q, check the boundary for all 4 directions and if the value is not 1, continue
- if value is 1, change it to 2 meaning good orange rottens and decrement the fresh and push it to the q
- return minute if fresh is 0 else -1
