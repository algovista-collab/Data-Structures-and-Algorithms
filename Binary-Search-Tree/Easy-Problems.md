## Validate BST: TC - O(N), SC - O(N)
- https://leetcode.com/problems/validate-binary-search-tree/description/
- call a helper function with root, nullptr, nullptr (denoting left and right subtree)
- if (left and root->val <= left->val) or if (right && root->val >= right->val) return false
- call helper with root->left, left, root && root->right, root, high

## Inorder Successor in BST: TC - O(N), SC - O(1)
- https://leetcode.com/problems/inorder-successor-in-bst/description/
- run a loop until root is empty, if p->val >= root->val then greater value is in the right subtree, root = root->right
- else root can be successor (successor = root) and root = root->left

## BST Iterator: TC - O(N), SC - O(N)
- https://leetcode.com/problems/binary-search-tree-iterator/description/
- stack<TreeNode*> st to store all the nodes and constructor calls pushToStack function
- pushToStack adds the elements in the leftmost branch to the stack
- next returns the top element in the stack, and if node->right, call the pushToStack(node->right)
- hasNext returns false if stack is empty

## Insert into a BST: TC - O(H), SC - O(1)
- https://leetcode.com/problems/insert-into-a-binary-search-tree/description/
- keep a prev pointer to root and next as prev, run a while loop until root is empty
- go to left or right depending on the value, store the new root in prev
- once loop ends, prev->val > val then prev->left = node else prev->right = node and return next

## Delete node in a BST: TC - O(logN), SC - O(H)
- https://leetcode.com/problems/delete-node-in-a-bst/description/
- base case: if root is the node to be deleted, call helper function with root and return helper(root)
- call deleteNode for both left and right subtree and finally return root
- helper function deletes the nodes and returns right if left is null else returns left
- go to the leftmost in the right subtree and return the right child

## Kth Largest Element in the Stream: TC - O((M + N) * logk), SC - O(k)
- https://leetcode.com/problems/kth-largest-element-in-a-stream/description/
- create priority_queue<int, vector<int>, greater<>> pq and int size
- KthLargest has a for loop, push the num into pq and while pq.size() > k pq.pop()
- add function, will push the val to pq and if pq.size() > size, pop and return pq.top()

## LCA of a BST: TC - O(N), SC - O(1)
- https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/
- run a while loop until root is empty (in the case return nullptr)
- if both p->val > root->val and q->val > root->val, root = root->right
- else if p->val < root->val and q->val < root->val, root = root->left
- else return root
