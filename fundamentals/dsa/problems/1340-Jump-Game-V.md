# 1340. Jump Game V

**Intution**
- From here, how far can I expand left and right until I hit a wall?

```python
class Solution:
    def maxJumps(self, arr: List[int], d: int) -> int:
        n = len(arr)
        memo = [0] * n

        def dfs(i):
            if memo[i] != 0:
                return memo[i]

            best = 1 

            for step in range(1, d + 1):
                ni = i + step
                if ni >= n or arr[ni] >= arr[i]:
                    break
                best = max(best, 1 + dfs(ni))

            for step in range(1, d + 1):
                ni = i - step
                if ni < 0 or arr[ni] >= arr[i]:
                    break
                best = max(best, 1 + dfs(ni))

            memo[i] = best
            return best

        return max(dfs(i) for i in range(n))
```

**Topics**
- [[dfs]]
- [[dp]]