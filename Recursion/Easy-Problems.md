## Space Complexity: Recursion
- The two main parts of the space consumption is recursion related space and non recursion related space
- Recursion related space refers to the memory cost incurred directly by the recursion that holds 3 pieces of information: returning address of the function call, parameters passed and the local variables
- Non recursion related space refers to global variables

## Tail Recusion

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

## Pow(x, n): TC - O(logn), SC - O(1)
- https://leetcode.com/problems/powx-n/description/
- run a loop until n > 0, keep ans = 1 initially
- if n%2 == 1, we need to keep x separated i.e. ans = ans * x
- n = n/2 and since n gets divided by 2 everytime, take square x = x * x
- this is multiplied with ans for the above condition when n%2 == 1
