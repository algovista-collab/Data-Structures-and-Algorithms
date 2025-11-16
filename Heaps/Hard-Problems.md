## K Closest Points to Origin (TO_DO)
- https://leetcode.com/problems/k-closest-points-to-origin/description/
- Binary Search approach and Quick select approach

## Furthest Building You can Reach
- https://leetcode.com/problems/furthest-building-you-can-reach/description/

## Merge k Sorted Lists: TC - O(N * logk), SC - O(k)
- https://leetcode.com/problems/merge-k-sorted-lists/description/
- lambda function that returns true if l should come after r
- auto cmp = [] (ListNode* l, ListNode* r) { return l->val > r->val; };
- priority_queue<ListNode*, vector<ListNode*>, decltype(cmp)> pq(cmp);
- push all the listnode heads in lists to pq and run a loop until pq is empty
- pop from pq, put it to result and if the next is present push it to the pq

## 
