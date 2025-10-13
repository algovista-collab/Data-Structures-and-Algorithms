# 🧩 Graphs and Disjoint Set Data Structure

## 1. Types of Graphs

### 🔹 Undirected Graph
- Edges between any two vertices do **not** have a direction.  
- Represents a **two-way** relationship.

### 🔹 Directed Graph
- Edges have a **direction**.
- Represents a **one-way** relationship.

### 🔹 Weighted Graph
- Each edge has an associated **weight** (like time, distance, or cost).

---

## 2. Negative Weight Cycle
In a **weighted graph**, a **negative weight cycle** exists if the sum of all the edge weights in a cycle is **negative**.


---

## 3. Degree of a Vertex

### 🟢 In Undirected Graphs
- **Degree** = Number of edges connected to a vertex.

### 🟣 In Directed Graphs
- **In-degree** = Number of edges **coming into** a vertex.  
- **Out-degree** = Number of edges **going out of** a vertex.

---

## 4. Disjoint Set Data Structure (Union-Find)

A **Disjoint Set (Union-Find)** is used to keep track of which elements are in the same connected component of a graph.  
It is especially useful in problems involving **connectivity**, such as:
- Computer networks
- Social networks
- Kruskal’s Minimum Spanning Tree algorithm

### 🧠 Key Concept
- Each element points to a **parent**.
- The **root node** is a parent to itself.
- Two vertices are **connected** if they share the same root.

---

## 5. Core Functions

| Function | Purpose |
|-----------|----------|
| `find(x)` | Finds the **root (representative)** of the set containing `x`. |
| `union(x, y)` | Merges (unions) the sets containing `x` and `y`. |

---

## 6. Implementations

### ⚡ Quick Find
- Stores the root of each element **directly** in an array.
- `find()` → **O(1)** (constant time)
- `union()` → **O(n)** (needs to update all elements in a set)

### ⚙️ Quick Union
- Each element points to its **parent**.
- The root is an element that points to **itself**.
- `find()` → **O(n)** in the worst case  
- `union()` → Calls `find()` twice → **O(n)**  
- More efficient than Quick Find in balanced trees.

---

## 7. C++ Implementation — Disjoint Set (Union-Find)

```cpp
class UnionFind {
public:
    UnionFind(int sz) : root(sz) {
        for (int i = 0; i < sz; i++) {
            root[i] = i;
        }
    }

    int find(int x) {
        return root[x];
    }

    int find(int x) {
        while (x != root[x]) {
            x = root[x];
        }
        return x;
    }

    void unionSet(int x, int y) {
        int rootX = find(x);
        int rootY = find(y);
        if (rootX != rootY) {
            for (int i = 0; i < root.size(); i++) {
                if (root[i] == rootY) {
                    root[i] = rootX;
                }
            }
        }
    }

    void unionSet(int x, int y) {
        int rootX = find(x);
        int rootY = find(y);
        if (rootX != rootY) {
            root[rootY] = rootX;
        }
    }

    bool connected(int x, int y) {
        return find(x) == find(y);
    }

private:
    vector<int> root;
};
```

