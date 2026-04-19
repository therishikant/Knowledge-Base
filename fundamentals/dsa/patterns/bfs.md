# BFS
- Move one step at a time in all direction
- Usefull when want to find min-steps required
- queue is used

```python
steps = 0
visited = set()
q = deque()

while q:
    size = len(q)
    for _ in range(size):
        node = q.popleft()
        if valid_node:
            visited.add(node)
            check_end_condition()
            added_new_node_queue()
    steps += 1
```

**Used_In**
- [[dp]]
- [[graph]]