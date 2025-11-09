## Kth Largest Element in an Array: TC - O(N*logK), SC - (K)
- https://leetcode.com/problems/kth-largest-element-in-an-array/description/
- Use min heap and keep pushing -num to the heap, if the size > k then pop and return -heap.top()

## Kth Largest Element in a Stream: TC - O(N*logK), SC - (K)
- https://leetcode.com/problems/kth-largest-element-in-a-stream/description/
- Keep priority_queue<int, vector<int>, greater<>> pq;
- Kth largest function, push the num to pq and if size > k, pop
- add function, push the val to pq and pop if size > k and return pq.top()

## Last Stone Weight: TC - O(), SC - O()
- https://leetcode.com/problems/last-stone-weight/description/
- Keep maxHeap and push all the stones and run a loop until only one stone or less is remaining
- maxHeap.top() will return the heaviest stone, remove 2 stones every loop and push their difference if they are not of same weight
- if heap is not empty, return the top element else 0
