## Kth Largest Element in an Array: TC - O(N*logK), SC - (K)
- https://leetcode.com/problems/kth-largest-element-in-an-array/description/
- Use min heap and keep pushing -num to the heap, if the size > k then pop and return -heap.top()
- -num is used because C++ default is maxHeap

## Kth Largest Element in a Stream: TC - O(N*logK), SC - (K)
- https://leetcode.com/problems/kth-largest-element-in-a-stream/description/
- Keep priority_queue<int, vector<int>, greater<>> pq;
- Kth largest function, push the num to pq and if size > k, pop
- add function, push the val to pq and pop if size > k and return pq.top()

## Last Stone Weight: TC - O(N*logN), SC - O(N)
- https://leetcode.com/problems/last-stone-weight/description/
- Keep maxHeap and push all the stones and run a loop until only one stone or less is remaining
- maxHeap.top() will return the heaviest stone, remove 2 stones every loop and push their difference if they are not of same weight
- if heap is not empty, return the top element else 0

## Meeting Rooms II: TC - O(N*logN), SC - O(N)
- https://leetcode.com/problems/meeting-rooms-ii/description/
- sort the intervals based on their starting time, we start allocating rooms to those who start early
- sort(intervals.begin(), intervals.end(), [](auto &a, auto &b) {return a[0] < b[0];})
- we keep minHeap and add the end time of the first meeting and run a for loop from i = 1
- if the second meeting start time is greater than first meeting end time, then it starts later so we can use the same room hence we pop from minHeap
- else we add the second meeting end time to the heap and so on. The size of the heap is the rooms we need.

## K Closest Points to Origin: TC - O(N*logK), SC - (N)
- https://leetcode.com/problems/k-closest-points-to-origin/description/
- calculate the squared distance and push it to the maxHeap as {distance, index}
- pop from the maxHeap if the size is > k and run a loop until heap is empty
- push the points[idx] to answer vector and return the answer

## Minimum Cost to Connect Sticks: TC - O(N*logN), SC - O(N)
- https://leetcode.com/problems/minimum-cost-to-connect-sticks/description/
- using greedy algorithm: push all the sticks to minHeap, run a while loop until the minHeap size > 1
- remove the top 2 elements, add it to the cost and push it to the minHeap and finally return the cost
