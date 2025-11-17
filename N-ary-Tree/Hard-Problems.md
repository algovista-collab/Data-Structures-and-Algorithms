## Encode N-ary Tree to Binary Tree: TC - O(n), SC - O(n)
- https://leetcode.com/problems/encode-n-ary-tree-to-binary-tree/description/
- Encode: keep a queue to store pairs of Binary node and N-ary node
- Create a new binary root from N-ary root and push both to the queue
- run a while loop until queue is empty, keep head and prev TreeNode pointers
- run a for loop over N-ary node and create a new TreeNode for every child
- if prev != nullptr, prev->right = bChild else head = bChild
- push both N-ary child and bChild to queue and after for loop, set bNode->left = head
- Decode: keep a queue to store pairs of N-ary node and Binary node
- Create a new N-ary root from binary root by passing vector<Node*> {} for children, push both to the queue
- run a while loop until queue is empty, set sibling = bNode->left
- run a inner while loop over sibling->right, create new N-ary child every loop and push it to children
- push both to the queue and finally return newRoot

## Serialize and Deserialize N-ary: TC - O(n), SC - O(n)
- https://leetcode.com/problems/serialize-and-deserialize-n-ary-tree/description/
- Main idea is to store as value[child[child]...]
- Serialize: create a string res = to_string(root->val) and add "["
- loop over its children, call serialize for every child which adds children recursively
- once loop ends, close it with "["
- Deserialize: keep a pos pointer for data and call helper function
- first create a value, run a loop until isdigit(data[pos]) and val = val * 10 + (data[pos] - '0')
- Create a node with this value and for children, increment pos and check if data[pos] != ']', call helper
- increment pos inside this loop, return node once loop ends
