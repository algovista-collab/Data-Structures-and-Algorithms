# 🌳 Binary Tree Traversals [For any problem in BT, think if you want to deal with children then come to node i.e. postorder or preorder or level order)

## ⚙️ Recursion (All O(n) time, O(n) space)
**Base case:** if `root == NULL` → return

### 🔹 Preorder (Root → Left → Right)
- Add `root->val` → recurse left → recurse right

### 🔹 Inorder (Left → Root → Right)
- Recurse left → add `root->val` → recurse right

### 🔹 Postorder (Left → Right → Root)
- Recurse left → recurse right → add `root->val`

---

## ⚙️ Iterative (Stack) – O(n) time, O(n) space

### 🔹 Preorder
- While stack not empty or curr not null  
  → Push curr, add val to result, go to left
  → When null, pop + move to right

### 🔹 Inorder
- While stack not empty or curr not null  
  → Go left pushing nodes  
  → When null, pop + add val to result → move to right

### 🔹 Postorder
- Use a stack + visited flag 
  → Go left pushing nodes to stack
  → When null, check if right exists → If yes, then set curr as curr->right, If no or visited==curr->right, then add to the result, set flag as curr, pop and set curr as null
  
---

## ⚙️ Morris Traversal (O(n) time, **O(1)** space)

### 🔹 Inorder
- While curr != NULL  
  → If no left, add val → move right  
  → Else find right most node of the left child, connect its right to the curr, set curr to curr->left
  → If right is already connected to curr, set to null, push the val to the result and move to right

### 🔹 Preorder
- Similar, but add val **before** moving left  
  (When creating thread)

---

## ⚙️ Level Order (BFS)
- Use queue (O(n) time, O(n) space)  
  → Push root  
  → While queue not empty: pop front, add val to the result, push left & right if present

## Height of a Binary Tree
```cpp
int maxDepth(TreeNode* root) {
    if (!root) return 0;
    return 1 + max(maxDepth(root->left), maxDepth(root->right));
}
```

## Balanced Binary Tree
- In the helper function, calculate the left subtree height and the right subtree height, if either of them is -1 then return -1
- Else, check if their difference is greater than 1, if yes return -1
- In the main function, return true if not equal to -1 from helper, else return false

## Preorder, Inorder and Postorder in One Traversal
- stack<pair<Node*, int>> st;
- Push the root, 1
- Loop until stack becomes empty, if st.second is 1, pop, add to preorder, increment and push back to the stack. If left child present, then push it with 1
- If st.second is 2, pop and add to inorder, increment and push back to stack. If right child present, then push it with 1
- If st.second is 3, pop and add to postorder

## Check if same tree or symmetric tree
- https://leetcode.com/problems/same-tree/description/
- If both are null, return true
- If either one if null, return false
- Compare the values && call the function with t1->left, t2->right && call the function with t1->right, t2->left

## Lowest Common Ancestor
- https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/
- Return root if root is null or root is p or root is q
- Recursive function call with left, and right
- If left subtree is null, return right
- If right subtree is null, return left
- If both are not null, return root

## Diameter of Binary Tree
- https://leetcode.com/problems/diameter-of-binary-tree/description/
- In the main function, set a diameter as 0 and pass it as reference to the helper along with the root
- In the helper function, call with left and right to get the height of both subtrees
- After receiving the height of both subtrees, update the diameter if left_height + right_height is greater than the diameter

## Maximum Path Sum
- https://leetcode.com/problems/binary-tree-maximum-path-sum/description/
- Similar to the diameter problem, have a global variable for the pathSum initialized to INT_MIN and update it in the helper function
- If leaf node, returns 0 otherwise return root->val + max(left_sum, right_sum)
- left_sum = max(0, helper(root->left)) do not consider negative values
- right_sum = max(0, helper(root->right)) do not consider negative values
- Update the pathSum if (root->val + left_sum + right_sum) is greater

## Printing the path from the root node to the given node
- We deal with the root first, then children hence its preorder
- Add the root->val to the result and if its the given node return true
- Else, call the left child if it returns true, stop otherwise call right child and return true if right child returns true
- Else, pop_back the value from the result and return false
- Finally return the result

## Populate the next pointers: TC - O(n), SC - O(1)
- https://leetcode.com/problems/populating-next-right-pointers-in-each-node/description/
- start with root, loop until its left child becomes null, inside the loop, loop again until head becomes null
- in the inner loop, head->left->next = head->right. if (head->next) head->right->next = head->next->left. Then assign, head = head->next
- outside the inner loop, loop the outer loop over root = root->left

## Count univalue subtrees
- https://leetcode.com/problems/count-univalue-subtrees/description/
- Helper function called with root and count variable
- Call the left and right child, then deal with the parent
- if root is null, return true, else
- check if both left and right are true, if yes then check if root->val == left->val and right->val, then return true else false
- if either of them are false, return false
