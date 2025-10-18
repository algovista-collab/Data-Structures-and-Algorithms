# Graphs and Disjoint Set Data Structure

## 1. Types of Graphs

### Undirected Graph
- Edges between any two vertices do **not** have a direction.  
- Represents a **two-way** relationship.

### Directed Graph
- Edges have a **direction**.
- Represents a **one-way** relationship.

### Weighted Graph
- Each edge has an associated **weight** (like time, distance, or cost).

---

## 2. Negative Weight Cycle
In a **weighted graph**, a **negative weight cycle** exists if the sum of all the edge weights in a cycle is **negative**.


---

## 3. Degree of a Vertex

### In Undirected Graphs
- **Degree** = Number of edges connected to a vertex.

### In Directed Graphs
- **In-degree** = Number of edges **coming into** a vertex.  
- **Out-degree** = Number of edges **going out of** a vertex.

---

## 4. Disjoint Set Data Structure (Union-Find)

A **Disjoint Set (Union-Find)** is used to know whether 2 vertices are connected efficiently.
It is especially useful in problems involving **connectivity**, such as:
- Computer networks
- Social networks
- Kruskal’s Minimum Spanning Tree algorithm

### Key Concept
- Each element points to a **parent**. Initially each element is its own parent.
- The **root node** is a parent to itself.
- Two vertices are **connected** if they share the same root.
- Constructor is called to initialize the array and Connected function is called to check if 2 vertices are connected.
- Union function is called to merge the vertices and find is called to return the root node. These can be implemented in 4 different ways.

---

## 5. Implementations

### Quick Find
- Stores the root of each element **directly** in an array.
- `find()` → **O(1)** (constant time)
- `union()` → **O(n)** (needs to update all elements in a set)

### Quick Union
- Each element points to its **parent**.
- The root is an element that points to **itself**.
- `find()` → **O(n)** in the worst case  
- `union()` → Calls `find()` twice → **O(n)**  
- More efficient than Quick Find in balanced trees.

### Union by rank
- Rank is the height of a node, smaller trees are merged into larger trees
- Time Complexity: Constructor: O(n), find: O(logn), union: O(logn), connected: O(logn). Space Complexity: O(n)

### Path Compression Optimization
- Initially, array stores the node's direct parent but when we call find function using recursion it stores the root node and returns it
- Next time when called that node, it only has to recurse twice to return the root node
- Time Complexity: Constructor: O(n), find: O(alpha(n)), union: O(alpha(n)), connected: O(alpha(n)). Space Complexity: O(n). alpha is Inverse Ackermann function that is almost O(1) complexity
- For this, we combine Union by rank and Path Compression

---

## 6. C++ Implementation — Disjoint Set

```cpp
class UnionFind {
public:
    UnionFind(int sz) : root(sz) {
        for (int i = 0; i < sz; i++) {
            root[i] = i;
            rank[i] = 1; # for Union by Rank implementation
        }
    }

    # Quick Find Implementation
    int find(int x) {
        return root[x];
    }

    # Quick Union Implementation and Union by Rank
    int find(int x) {
        while (x != root[x]) {
            x = root[x];
        }
        return x;
    }

    # Path Compression Optimization
    int find(int x) {
        if (x == root[x]) return x;
        return root[x] = find(root[x]);
    }

    # Quick Find Implementation
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

    # Quick Union Implementation
    void unionSet(int x, int y) {
        int rootX = find(x);
        int rootY = find(y);
        if (rootX != rootY) {
            root[rootY] = rootX;
        }
    }

    # Union by Rank Implementation
    void unionSet(int x, int y) {
        int rootX = find(x);
        int rootY = find(y);
        if (rootX != rootY) {
            if (rank[rootX] < rank[rootY]) root[rootX] = rootY;
            else if (rank[rootX] > rank[rootY]) root[rootY] = rootX;
            else: root[rootY] = rootX; rank[rootX] += 1
        }
    }

    bool connected(int x, int y) {
        return find(x) == find(y);
    }
};
```

## 7. Valid Tree in a Graph
- There is a path and only one path between every node in the graph
- The graph has no cycles, so edges = n-1.
- If edges < n-1, must be disconnected and if edges > n-1, must contain cycle

# 8. Graph Representation

Graphs can be represented mainly in two ways:
1. **Adjacency Matrix**
2. **Adjacency List**

---

## 1. Adjacency Matrix
- A 2D array `graph[n][n]` where `graph[i][j]` represents the **presence or weight** of an edge from node `i` to node `j`.

---

```text
Initialize matrix graph[n][n] with 0
TC - O(V^2), SC - O(V^2)
For each edge (u, v):
    if undirected:
        graph[u][v] = 1
        graph[v][u] = 1
    if directed:
        graph[u][v] = 1
    if weighted (directed or undirected):
        graph[u][v] = weight
        if undirected:
            graph[v][u] = weight
```

## 2. Adjacency List
- An array (or list) of lists where each index i contains a list of neighbours of node i.
- For weighted graphs, each neighbour is stored as a (node, weight) pair.

```text
Initialize vector<int> adj[n+1] with 0
TC - O(V+E), SC - O(V+E)
vector<int> adj[n+1];

// For each edge (u, v):
if undirected:
    adj[u].push_back(v);
    adj[v].push_back(u);
else if directed:
    adj[u].push_back(v);

// For each edge (u, v, weight):
if undirected:
    adj[u].push_back({v, weight});
    adj[v].push_back({u, weight});
else if directed:
    adj[u].push_back({v, weight});
```
