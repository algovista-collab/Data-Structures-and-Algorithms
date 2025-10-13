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
#include <bits/stdc++.h>
using namespace std;

class DisjointSet {
    vector<int> parent, rank;

public:
    // Constructor
    DisjointSet(int n) {
        parent.resize(n);
        rank.resize(n, 0);
        for (int i = 0; i < n; i++) {
            parent[i] = i;  // each node is its own parent initially
        }
    }

    // Find function with path compression
    int find(int x) {
        if (parent[x] == x)
            return x;
        return parent[x] = find(parent[x]); // path compression
    }

    // Union function by rank
    void unionByRank(int u, int v) {
        int rootU = find(u);
        int rootV = find(v);

        if (rootU == rootV)
            return; // already connected

        if (rank[rootU] < rank[rootV]) {
            parent[rootU] = rootV;
        } else if (rank[rootU] > rank[rootV]) {
            parent[rootV] = rootU;
        } else {
            parent[rootV] = rootU;
            rank[rootU]++;
        }
    }
};

int main() {
    DisjointSet ds(7);

    ds.unionByRank(1, 2);
    ds.unionByRank(2, 3);
    ds.unionByRank(4, 5);
    ds.unionByRank(6, 7);
    ds.unionByRank(5, 6);

    // Check connectivity
    if (ds.find(3) == ds.find(7))
        cout << "Same component\n";
    else
        cout << "Different components\n";

    ds.unionByRank(3, 7);

    if (ds.find(3) == ds.find(7))
        cout << "Now in the same component\n";
    else
        cout << "Still different\n";

    return 0;
}
```

