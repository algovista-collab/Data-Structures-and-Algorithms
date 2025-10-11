# 🌳 Binary Tree Traversals (Quick Revision)

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
  → When null, check if right exists → If yes, then set curr as curr->right, If no, then add to the result, set flag as curr, pop and set curr as null
  
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
- if both are null, return true
- if either one if null, return false
- Compare the values && call the function with t1->left, t2->right && call the function with t1->right, t2->left
