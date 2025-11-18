## Kth Smallest Element in a Sorted Matrix: TC - O(), SC - O()
- https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/description/

## Find Median from Data Stream: TC - , SC - 
- https://leetcode.com/problems/find-median-from-data-stream/description/

## Top K Frequent Elements: TC - O(N), SC - O(N)
- https://leetcode.com/problems/top-k-frequent-elements/description/
- Use quick select,

## The K Weakest Rows in a Matrix: TC - , SC - 
- https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/description/

## Task Scheduler
- https://leetcode.com/problems/task-scheduler/description/

## Hands of Straights
- https://leetcode.com/problems/hand-of-straights/description/
  
## Find K Pairs with Smallest Sums: TC - O(k*logk), SC - O(k)
- https://leetcode.com/problems/find-k-pairs-with-smallest-sums/description/
- minHeap to store the sum and pair of indices and visited to store the pair of indices
- after every pair, (i+1, j) or (i, j+1) is the smallest and hence we push them to the heap
- first push the pair (0,0) in minHeap and visited, run a loop until k==0 and minHeap is empty
- pop and put the pair in the answer vector, check the conditions for next 2 pairs and push to the heap

## Merge intervals: TC - O(N*logn), SC - O(n)
- https://leetcode.com/problems/merge-intervals/description/
- sort the intervals based on startTime and loop over intervals
- if merged is empty or merged.back()[1] is less than interval[0] then there is no overlap so push the interval
- else update the merged.back()[1] to max(merged.back()[1], interval[1])

## Insert Interval: TC - O(n), SC - O(n)
- https://leetcode.com/problems/insert-interval/description/
- using binary search, if (intervals[mid][0] < newInterval[0]) left = mid+1 else right = mid-1
- once the spot is known, insert the newInterval like intervals.insert(intervals.begin()+left, newInterval)
- do the same as in the problem merge intervals

## Minimum Number of Arrows to Burst Balloons: TC - O(N*logN), SC - O(1)
- https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/
- shoot the balloons those come under maximum xEnd, hence sort by xEnd and initialize arrow = 1 and end to first points[1]
- run a loop over points, if the current xStart > previous xEnd, then we need new arrow and also update end to current end

## Maximum Number of Events that can be attended: TC - O(N*logN), SC - O(N)
- https://leetcode.com/problems/maximum-number-of-events-that-can-be-attended/description/
- using greedy algorithm and minHeap, first sort the events based on their start day
- start with i = 1, i.e. day 1 and run a loop until j < n or pq is not empty
- put all the events end day whose start day is <= i (we can consider attending those events), minHeap keeps the event with smaller end day
- remove all the events whose end day < i (we cannot attend those events)
- if pq is still not empty, increment the answer

## Non-overlapping intervals: TC - O(N*logN), SC - O(N)
- https://leetcode.com/problems/non-overlapping-intervals/description/
- We remove the intervals with higher end time, hence sort the intervals by their endtime
- initially k=INT_MIN, run a loop over intervals and if the start time is >= k then there is no overlap, set k = curr end time
- else increment the answer because there is overlap and we are removing the intervals with higher end time 
