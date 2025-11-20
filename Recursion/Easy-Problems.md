## Reverse Strings: TC - O(N), SC - O(N for recursion)
- https://leetcode.com/problems/reverse-string/description/
- call helper with start and end, simply swap the s[start] and s[end]

## Sort Colors: Dutch National Flag Algorithm - TC: O(N), SC - O(1)
- https://leetcode.com/problems/sort-colors/description/
- the idea is to keep the 3 pointers: p0 to p1 as 0, p1 to p2 as 1 and p2 to end as 2
- initially p0 and p1 is 0 and p2 as n-1, run a loop until p1 <= p2
- if p1 == 0, swap p1,p0 and increment both
- if p1 == 2, swap p1,p2 and decrement p2
- if p1 == 1, increment p1
