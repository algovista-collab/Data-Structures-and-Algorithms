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
