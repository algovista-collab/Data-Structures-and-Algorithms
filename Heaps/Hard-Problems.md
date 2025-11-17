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

## Process Tasks using Servers: TC - O(M*logN + N*logN), SC - O(M+N)
- https://leetcode.com/problems/process-tasks-using-servers/description/
- keep 2 priority queues - available stores weight and serverIndex, busy stores freeTime of server and its index
- push all the server weight and index to available and keep long long time = 0 to begin
- run a for loop over all tasks and res(m) vector for the result
- Case 1: servers to be freed
  * if busy is not empty and its top servers's free time is <= time, it can be freed, hence pop and push it to available
- Case 2: if available is empty, shift the time to the top server's free time and pop all servers from busy if their freeTime <= time and push to available
- pop the available server and push its index to the result and push time+tasks[i], serverIndex to busy

## IPO: TC - O(n*logn), SC - O(n)
- https://leetcode.com/problems/ipo/description/
- vector<pair<int,int>> pairs and pairs.emplace_back(capital[i], profits[i])
- pairs will store the capital and profit of a project and sort it to store capital in ascending order
- keep a pointer to first project of pairs and maxHeap to store affordable projects with higher profit at the top
- run a for loop k times and push every project whose capital <= w to the maxHeap
- if maxHeap is empty, there are no projects available hence break, else pop and add the profit to the w

## Sliding Window Median: TC - O(N*logK), SC - O(K)
- https://leetcode.com/problems/sliding-window-median/description/
- each loop has erase, insert in multisets and loop runs over n times hence N*logK is the time complexity
- keep 2 multisets, small for first half of the array and large for second half of the array
- both multisets should be balanced, i.e. small.size() == large.size() + 1 or small.size() == large.size()
- Step 1: inserting elements either in small or large, if small is empty or current element is smaller than *small.rbegin(), insert to small else to large
- Step 2: if window exceeds k (i >= k) find(nums[i-k]) in small, if found erase (small.erase(small.find(nums[i-k]) else erase from large
- Step 3: sets become imbalance, remove from either of them and put it to the other (while small.size() > large.size() + 1)
- Step 4: find a median when i >= k-1, if k is even then put the average else *small.rbegin()
- Multiset is used instead of PQ because we need to remove nums[i-k] which is an arbitrary element and removing from PQ is not efficient
- Multiset, insert is logk, find is logk, erase by iterator is O(1)
