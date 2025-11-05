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
