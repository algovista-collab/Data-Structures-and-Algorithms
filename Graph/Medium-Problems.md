## Smallest String With Swaps
- https://leetcode.com/problems/smallest-string-with-swaps/description/
- TC - O((V+E)alpha(V) + V logV) [V-length of the string], SC - O(V)
- Build the root and rank using DSU functions
- Create an unordered_map with int as key and vector<int> as values
- Loop over length of string and find the root of every index and make it a key and push the index as values
- Every element in the map are connected and can be swapped - we need to sort them
- Loop over the map, collect the characters corresponding to the indices in the map and sort them and store them in the result string based on their index
