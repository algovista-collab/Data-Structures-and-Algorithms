## Traversal
- **Preorder**: We start with the root node, go to its children until leaf node, then go to the other children
- Inorder traversal does not make sense in N-ary tree
- **Postorder**: We go to the leaf node of one child, then traverse back to root and so on
- **Level**: Similar to Binary Tree

## Preorder and Postorder
```cpp
vector<int> preorder(Node* root) {
        if (!root) return {};
        stack<Node*> st;
        vector<int> res;
        st.push(root);
        while (!st.empty()) {
            Node* node = st.top(); st.pop();
            res.push_back(node->val);
            # preorder
            for (int i = node->children.size()-1; i >= 0; i--) {
                st.push(node->children[i]);
            }

            # postorder
            for (Node* child: node->children) {
                st.push(child);
            }
        }
        # postorder
        reverse(res.begin(), res.end());
        return res;
```

## Max Depth
```cpp
        int depth = 0;
        for (Node* node: root->children) {
            depth = max(depth, maxDepth(node));
        }
        return 1+depth;
```
