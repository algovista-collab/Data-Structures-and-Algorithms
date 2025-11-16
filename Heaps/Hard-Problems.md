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

## Single Threaded CPU: TC - O(N*logN), SC - O(N)
- https://leetcode.com/problems/single-threaded-cpu/description/
- keep a minHeap to store {processTime, index}
- keep a vector to store enqueTime, processTime, index and sort it based on enqueTime
- currTime  = 0 and taskIndex = 0, run a while loop until tasksIndex < tasks.size() or heap is not empty
- if the heap is empty which means CPU is idle and currTime is less than task enqueTime, make currTime = enqueTime
- push all the tasks whose enque time is less than currTime to process them next in the loop
- push them to the heap and increment the taskIndex
- pop the heap and increase the currTime to the processTime and push the index to the answer

## Process Tasks using Servers:
- https://leetcode.com/problems/process-tasks-using-servers/description/
- 
