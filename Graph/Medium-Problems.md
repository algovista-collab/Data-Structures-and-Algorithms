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
