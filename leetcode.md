# leetcode

## sliding window
### 1. Longest Substring Without Repeating Characters
https://leetcode.com/problems/longest-substring-without-repeating-characters/description/?envType=featured-list&envId=top-interview-questions
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        seen = {} # to indicate the latest index of each char in s
        left = 0 # indicate left index of current sliding window
        ans = 0
        for i in range(len(s)):
            cur = s[i]
            if cur in seen.keys() and seen[cur] >= left: # if current char shown before and its within current sliding window, update the left index of current sliding window
                left = seen[cur] + 1
            else: # update the longest length
                ans = max(ans, i - left + 1)
            seen[cur] = i
        return ans
