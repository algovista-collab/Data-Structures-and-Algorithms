# 🌳 Binary Tree (Quick Notes)

- **N nodes → N-1 edges**

## 🔹 Types
- **Full BT**: Every node has 0 or 2 children  
- **Complete BT**: All levels filled except last (filled left→right)  
- **Perfect BT**: All internal nodes have 2 children + all leaves same level  
- **Balanced BT**: The maximum height difference between left and right subtree of any node is 1. Height = O(log n)  
- **Degenerate/Skewed**: Each node has 1 child → height = O(n)

**Height formulas:**  
- Min height = ⌊log₂ n⌋  
- Max height = n

## 🔹 C++ Representation
```cpp
struct Node {
    int data;
    Node* left;
    Node* right;
    Node(int val) : data(val), left(NULL), right(NULL) {}
};

## 🔹 Traversals
1. Depth First Search: Preorder (Root-Left-Right), Inorder (Left-Root-Right), Postorder (Left-Right-Root)
2. Breadth First Search: Level order 
