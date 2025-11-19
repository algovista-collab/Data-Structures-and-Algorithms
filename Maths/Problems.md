## Palindrome Number: TC - O(log10(n)), SC - O(1)
- https://leetcode.com/problems/palindrome-number/description/
- loop over number of digits (d = floor(log10(n), n is the number)
- for negative number and multiple of 10 except 0 return false
- loop over x > reversed (only reverse the second half to over overflow)
- reversed *= 10 + x % 10 and x = x / 10, return if x == reversed || x == reversed / 10 (for odd number of digits)

## Reverse Integer: TC - O(logX), SC - O(1)
- https://leetcode.com/problems/reverse-integer/description/
- multiply by 10 and add the remainder but we need to check if there is a overflow
- INT_MAX is 2^31-1 = 2147483647 and INT_MIN  is -2^31 = -2147483648
- if reversed > INT_MAX / 10 i.e. reversed = 214748365 (just one more) but we multiply by 10 in the next step = 2147483650 > INT_MAX
- if reversed == INT_MAX / 10, reversed = 214748364 then *10 + pop can lead to overflow, so we check if pop > 7, similar checking for negative numbers

## Max Points on a line: TC - O(n²), SC - O(n)
- https://leetcode.com/problems/max-points-on-a-line/description/
- distinct lines are identified by their slope and since double division is not precise, we use atan2 function (points on the same line has same atan2)
- atan2 is the angle measure between the positive x-axis and the ray from the origin to the point in the cartesian plane (https://en.wikipedia.org/wiki/Atan2)
- keep a unordered_map of slope and its count, run a for loop over points and initialize the map
- run inner for loop and calculate dx and dy for all the points for the given point in the outer for loop
- slope = atan2(dy,dx) and store in the map and update res = max(res, slope[s]+1)

## Valid Square: TC - O(1), SC - O(1)
- https://leetcode.com/problems/valid-square/description/
- check if all the points are distinct by storing them in the set<pair<int,int>> and return false if size is not 4
- 4 distinct points form a valid square when all the sides are equal and diagonals also have same length
- we calculate lengths of all 4 sides and 2 diagonals: square length = (x1-x2)*(x1-x2) + (y1-y2)*(y1-y2) and insert to set<int>
- if the set size is 2 (1 unique length for 4 sides and 1 unique length for 2 diagonals) then they form a square else return false
