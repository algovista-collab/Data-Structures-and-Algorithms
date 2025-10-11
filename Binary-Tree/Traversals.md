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
  → Go left, push curr, add val to result  
  → When null, pop + move to right

### 🔹 Inorder
- While stack not empty or curr not null  
  → Go left pushing nodes  
  → When null, pop + add val → move to right

### 🔹 Postorder
- Use 2 stacks (or 1 stack + visited flag)  
  → Push root, process right before left  
  → Reverse result

---

## ⚙️ Morris Traversal (O(n) time, **O(1)** space)

### 🔹 Inorder
- While curr != NULL  
  → If no left, add val → move right  
  → Else find predecessor → make thread → move left  
  → When thread found, remove it → add val → move right

### 🔹 Preorder
- Similar, but add val **before** moving left  
  (When creating thread)

---

## ⚙️ Level Order (BFS)
- Use queue (O(n) time, O(n) space)  
  → Push root  
  → While queue not empty: pop front, add val, push left & right
