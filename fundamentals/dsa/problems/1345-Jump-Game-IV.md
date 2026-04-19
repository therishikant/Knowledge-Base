# 1345. Jump Game IV

**Intution**
- Treat each index as node 
- You can move to +1, -1, and arr[i] == arr[j] 
- Do BFS  
- Create adj list of (arr[i], i)  

```python
class Solution:
    def minJumps(self, arr: List[int]) -> int:
        n = len(arr)
        visited = set()
        num_index = defaultdict(list)
        q = deque()
        for i in range(n): 
            num_index[arr[i]].append(i)
        steps = 0
        q.append(0)
        while q:
            size = len(q)
            for _ in range(size):
                i = q.popleft()
                if i in range(n) and i not in visited:
                    if i == n-1:
                        return steps
                    q.append(i+1)
                    q.append(i-1)
                    if num_index[arr[i]][0] not in visited:
                        for idx in num_index[arr[i]]:
                            q.append(idx)
                    visited.add(i)
            steps += 1
        
```

**Topics**
- [[bfs]]