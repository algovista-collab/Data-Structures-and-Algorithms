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

## My Calendar II: TC - O(N), SC - O(N)
- https://leetcode.com/problems/my-calendar-ii/description/
- Line Sweep algorithm can be used to solve both calendar I and II, it keep a an ordered map - map<int, int>
- If 2 or more intervals fall in the same booking, then their start time like 10, 15, 17 come first whose value is 1 and end time -1
- when you run a for loop, count is incremented and initial start time are in the beginning and if there is overlap, count will be more than 2
- when count is more than 2, mpp[start]-- and mpp[end]++ and return false

## My Calender I: TC - O(N*logN), SC - O(N)
- lower_bound in set is binary search takes logN time and logN after inserting the event
- https://leetcode.com/problems/my-calendar-i/description/
- We keep set<pair<int,int>> calendar as data structure to store start and end time.
- store time in const pair<int,int> event and check calendar.lower_bound(event), will return the element in the calendar whose start time is greater or equal to event's start time
- check if nextEvent whose start time is greater has an endtime which is less than event's endtime. There is a overlapping, return false
- check if prev(nextEvent) has an endTime which is greater than event's starttime, return false, else insert return true

## Trim a BST: TC - O(N), SC - O(H)
- https://leetcode.com/problems/trim-a-binary-search-tree/description/
- if (root->val > high) return trimBST(root->left, low, high);
- if (root->val < low) return trimBST(root->right, low, high);
- root->left = trimBST(root->left, low, high); root->right = trimBST(root->right, low, high);
