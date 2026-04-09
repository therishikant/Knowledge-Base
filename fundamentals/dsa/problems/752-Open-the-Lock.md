# 752. Open the Lock

### Intution
#### 1. Backtracking
- Find every possible way, not efficent
- Not able to code
#### 2. BFS
- Go one by one treat each lock[i] as a node
- Add deadlocks into visited set at starting
- There will be 8 nodes from single lock position 4 in +1 and -1.

#### Pattern
- BFS 
- Backtracking

#### Mistakes
- Not able to code backtracking approch 
- Not able to think BFS approch
- 

#### Code
```python
class Solution:
    def openLock(self, deadends: List[str], target: str) -> int:
        if "0000" in deadends:
            return -1

        def childreen(lock):
            res = []
            for i in range(4):
                digit = str((int(lock[i]) + 1) % 10)
                res.append(lock[:i] + digit + lock[i+1:])
                digit = str((int(lock[i]) - 1 + 10) % 10)
                res.append(lock[:i] + digit + lock[i+1:])
            return res

        q = deque()
        visited = set(deadends)
        q.append(["0000", 0])

        while q:
            lock, turns = q.popleft()
            if lock == target:
                return turns
            for child in childreen(lock):
                if child not in visited:
                    visited.add(child)
                    q.append([child, turns + 1]) 
        return -1
```

