# 978. Longest Turbulent Subarray

**Intution**
- At each position, we track two values: 
  - the length of the turbulent subarray ending here with an increasing comparison, and 
  - the length ending with a decreasing comparison.
- When we see an increase, we extend the previous decreasing sequence (and vice versa), since turbulence requires alternation.

**Mistakes**
- Not able to code
- did range(1, n-1) but able to do in range(1, n)
- was comparing ((i-1) and (i+1)) but if we go for 2D-dp then it will solved with compare (i-1)
  
```python
class Solution:
    def maxTurbulenceSize(self, arr: List[int]) -> int:
        n = len(arr)
        dp = [[1] * 2 for _ in range(n)]

        res = 1
        for i in range(1, n):
            if arr[i] > arr[i-1]:
                dp[i][0] = dp[i - 1][1] + 1
            elif arr[i] < arr[i - 1]:
                dp[i][1] = dp[i - 1][0] + 1

            res = max(res, dp[i][0], dp[i][1])
        
        return res
```

**Topics**
- [[dp]]
- [[greedy]]