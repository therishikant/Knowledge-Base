# 45. Jump Game II

**Intution**
- Think of problem as 1D-BFS
- what is max we can reach from a window of index?
- do layer by layer
- **DP** solution could also work but tc(n^2)

**BFS**
```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        res = 0
        l = r = 0

        while r < len(nums) - 1:
            far = 0
            for i in range(l, r + 1):
                far = max(far, i + nums[i])
            l = r + 1
            r = far
            res += 1

        return res
```
**2D-dp**
```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        n = len(nums)
        dp = [1000000] * n
        dp[-1] = 0

        for i in range(n-2, -1, -1):
            end = min(n, i + nums[i] + 1)
            for j in range(i + 1, end):
                dp[i] = min(dp[i], 1 + dp[j])
        
        return dp[0]
```

**Topics**
- [[greedy]]
- [[bfs]]
- [[dp]]