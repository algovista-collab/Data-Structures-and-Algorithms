## Amount of time to infect or burn all the nodes: TC - O(n), SC - O(n)
- https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected/description/
- call the helper function with root, minute and infected node. Recursively call the left and right child, then deal with the root
- if the root is the infected node, update minute as minute = max(left_height, right_height) and set the depth as -1
- else if the left_height and right_height both are postive, simply return depth as max(l,r)+1
- else if either of them are negative which means this subtree has a infected node. Update minute as max(minute, abs(left_height)+abs(right_height)), that is the maximum distance of any node from the infected node. Return depth as min(left_height, right_height) - 1

## Serialize and Deserialize: TC - O(n), SC - O(n)
- https://leetcode.com/problems/serialize-and-deserialize-binary-tree/description/
- https://leetcode.com/problems/unique-binary-search-trees/description/
- Serialize - use queue data structure; if (node) ss.append(to_string(node->val) + ','); then push its left and right child even they are nullptrs
- If null, then ss.append("null,");
- Deserialize - we use stringstream ss(data). string token; getline(ss, token, ','). Use queue and push the root
- if getline is not null, node->left = new TreeNode(stoi(token)); again for node->right as well then push left and right to the queue

## All Nodes Distance K in Binary Tree: TC - O(n), SC - O(n)
- https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/description/
- 

## Count Complete Tree Nodes: TC - O(d²) = O((log n)²), SC - O(1)
- https://leetcode.com/problems/count-complete-tree-nodes/description/
- Compute depth - call only root->left until leaf node. Depth starts from 0
- In the last level, number of nodes is 2ᵈ. We index the nodes from 0 to 2ᵈ-1. Since we know last level has atleast one node, we start checking from left=1 upto right = 2ᵈ-1 (1 << d - 1) 
- Apply Binary Search - pivot = left + (right - left) / 2: if pivot exists that means the node exits - hence move the left to pivot+1, else right = pivot-1
- Return total number of nodes until last level (2ᵈ - 1) + nodes in the last level = left
- Exists function: Traverse from the root until the last level
- Binary search is applied again from left=0 to right = 2ᵈ-1 (last level indices), if the pivot is less than the mid of these, move to root->left, right = pivot
- If the pivot is greater than the mid of these, move to root->right, left = pivot+1
