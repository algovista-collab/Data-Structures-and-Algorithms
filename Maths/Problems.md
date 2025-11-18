## Palindrome Number: TC - O(log10(n)), SC - O(1)
- https://leetcode.com/problems/palindrome-number/description/
- loop over number of digits (d = floor(log10(n), n is the number)
- for negative number and multiple of 10 except 0 return false
- loop over x > reversed (only reverse the second half to over overflow)
- reversed *= 10 + x % 10 and x = x / 10, return if x == reversed || x == reversed / 10 (for odd number of digits)
