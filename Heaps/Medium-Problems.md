## Kth Smallest Element in a Sorted Matrix: TC - O(), SC - O()
- https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/description/

## Find Median from Data Stream: TC - , SC - 
- https://leetcode.com/problems/find-median-from-data-stream/description/

## Top K Frequent Elements: TC - O(N), SC - O(N)
- https://leetcode.com/problems/top-k-frequent-elements/description/
- Use quick select,

## The K Weakest Rows in a Matrix: TC - , SC - 
- https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/description/ 

## Find K Pairs with Smallest Sums: TC - O(k*logk), SC - O(k)
- https://leetcode.com/problems/find-k-pairs-with-smallest-sums/description/
- minHeap to store the sum and pair of indices and visited to store the pair of indices
- after every pair, (i+1, j) or (i, j+1) is the smallest and hence we push them to the heap
- first push the pair (0,0) in minHeap and visited, run a loop until k==0 and minHeap is empty
- pop and put the pair in the answer vector, check the conditions for next 2 pairs and push to the heap
