# 1834. Single-Threaded CPU

#### 1. Mistake
- Didn't do sorting 
- Not able to code effeciently TLE, no test case passed 

#### 2. Accepted Code
```python
class Solution:
    def getOrder(self, tasks: List[List[int]]) -> List[int]:
        heap = []
        res = []

        tasks = sorted([(eqTime, effort, i) for i, (eqTime, effort) in enumerate(tasks)])
        
        i = 0
        n = len(tasks)
        time = 0

        while heap or i < n:

            if not heap and time < tasks[i][0]:
                time = tasks[i][0]

            while i < n and tasks[i][0] <= time:
                eqTime, effort, idx = tasks[i]
                heapq.heappush(heap, (effort, idx))
                i += 1

            effort, idx = heapq.heappop(heap)
            res.append(idx)
            time += effort  

        return res
```