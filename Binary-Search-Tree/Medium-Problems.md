## Contains Duplicate III: TC - O(N), SC - O(min(N,k))
- https://leetcode.com/problems/contains-duplicate-iii/description/
- create unordered_map<int, int> buckets and w = valueDiff+1
- run a for loop over nums.size() and getId returns num < 0 ? (num-1) / w - 1 : num / w;
- in the loop, call getId for nums[i], w
- if (buckets.count(bucket)) return true;
- if (buckets.count(bucket-1) && abs(nums[i] - buckets[bucket-1]) < w) return true;
- if (buckets.count(bucket+1) && abs(nums[i] - buckets[bucket+1]) < w) return true;
- buckets[bucket] = nums[i]; and if (i >= indexDiff) buckets.erase(getId(nums[i-indexDiff], w));

>> Revise: https://leetcode.com/explore/learn/card/introduction-to-data-structure-binary-search-tree/143/appendix-height-balanced-bst/1021/

## Recover BST: TC - O(N), SC - O(1)
- https://leetcode.com/problems/recover-binary-search-tree/description/
- Using Morris Traversal: During inorder traversal, detect two nodes where the order breaks:
- If root->val < pred->val, we’ve found an inversion.
- First inversion → x = pred
- Second inversion → y = root
- After traversal, swap values of x and y.

## Merge BSTs to Create Single BST: TC - O(), SC - O()
- https://leetcode.com/problems/merge-bsts-to-create-single-bst/description/
  
## Stock Price Fluctuation: TC - O(), SC - O()
- https://leetcode.com/problems/stock-price-fluctuation/description/

## My Calendar II: TC - O(), SC - O()
- https://leetcode.com/problems/my-calendar-ii/description/

## My Calender I: TC - O(), SC - O()
- https://leetcode.com/problems/my-calendar-i/description/

## Trim a BST: TC - O(N), SC - O(H)
- https://leetcode.com/problems/trim-a-binary-search-tree/description/
- if (root->val > high) return trimBST(root->left, low, high);
- if (root->val < low) return trimBST(root->right, low, high);
- root->left = trimBST(root->left, low, high); root->right = trimBST(root->right, low, high);
