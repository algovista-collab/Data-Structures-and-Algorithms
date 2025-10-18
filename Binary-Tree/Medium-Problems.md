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

## Maximum Width: TC - O(n), SC - O(n)
- https://leetcode.com/problems/maximum-width-of-binary-tree/description/
- queue<pair<TreeNode*, long long>> stores root and level. The first node in every level can be stored at 0.
- push 2*index for left child and 2*index+1 for right child. q.front().second is stored in the minIndex to avoid the overflow
- when the for loop is entered, index = q.front().second - minIndex. So that every level starts from 0 and increases - because we only need the absolute difference between the extreme nodes in the same level and not the actual value

## Construct a Binary Tree from Inorder and Preorder/Postorder: TC  - O(n), SC - O(n)
- In the main function, create a map to store the index as value and element as key from inorder array
- Preorder first element is always the root and postorder last element is always the root - call the recursive function with pre/postorder, inorder, start and end
- Base case is when start > end, root is mpp[preorder[preStart]] or mpp[postorder[postStart]]
- inorder - inStart is number of elements on the left subtree and remaining on the right subtree
- Create a root, call the recursive function for left and right subtree with respective start and end

## Flatten Binary Tree: TC - O(n), SC - O(1)
- https://leetcode.com/problems/flatten-binary-tree-to-linked-list/description/
- Use Morris Traversal, but connect the rightmost node of the left child to the right child of the root
- while (root) -> if (root->left) go to rightmost node, rightmost->right = root->right, root->right = root->left, root->left = null
- Set root = root->right everytime
