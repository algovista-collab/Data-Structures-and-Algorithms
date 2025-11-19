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
