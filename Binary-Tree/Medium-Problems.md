## Vertical Order Traversal: TC - O(N logn), SC - O(N)
- https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/description/
- Data Structure: map<int, map<int, multiset<int>>> this stores a map at every column c, internal map stores for every c, elements at each level. Multiset sorts automatically with log(n). queue<pair<TreeNode*, pair<int, int>>> to store root with its vertical axis and level
- Map sorts based on vertical axis and internal map sorts based on the level, multiset sorts the values that are in the same level and vertical axis
- Store every axis into vector: temp.insert(temp.end(), level.second.begin(), level.second.end());

## Right or Left View: TC - O(N), SC - O(H)
- https://leetcode.com/problems/binary-tree-right-side-view/description/
- Call the helper function with root, result vector and the level
- If result vector size == level, push it. i.e. for every level from 0 push only one node to the result. Call root->right first then root->left

## Top View: TC - O(N), SC - O(N)
- map<int, int> stores only first node it encounter for every vertical axis. Hence in BFS, update the map only if that vertical axis is not present yet
- if (mpp.find(axis) == mpp.end()) mpp[axis] = node->val;

## Zig-Zag Traversal TC: O(n), SC: O(n) 
- https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/
- Level order traversal using queue, keep a flag to know the direction for a particular level
- Set a vector of size n, if flag is true start filling from left to right otherwise right to left

## Boundary Traversal TC: O(n), SC: O(n)
- https://leetcode.com/problems/boundary-of-binary-tree/description/
- Write 3 private functions for:
- LeftBoundary - return if node is null or a leaf node, else add to result, call its left child if absent, call right child
- LeafNodes - add to result if it is a leaf node, else call left and then right
- RightBoundary - return if node is null or a leaf node, else add to result, call its right child if absent, call left child
