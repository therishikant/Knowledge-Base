# 1871. Jump Game VII

**Intution**
- BFS
- no need to add same in index again (otherwise TLE)
- we only care about range(far + 1, max(i + maxJump, n-1))
- if reached n-1 and arr[i] == "0" return.

```python
class Solution:
    def canReach(self, s: str, minJump: int, maxJump: int) -> bool:
        n = len(s)
        far = 0
        q = deque()
        q.append(0)
        while q:
            i = q.popleft()
            start = max(i + minJump, far + 1)
            for j in range(start, min(i + maxJump+1, n)):
                if s[j] == "0":
                    if j == n - 1:
                        return True
                    q.append(j)
            far = i + maxJump

        return False
```

**Topic**
- [[bfs]]
- [[dp]]
- [[greedy]]