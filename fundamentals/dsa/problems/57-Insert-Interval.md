# 57. Insert Interval


**Mistake**
- didn't wrote a clean code

```python
class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        res = []
        for start, end in intervals:
            if newInterval[0] <= start <= newInterval[1] or newInterval[0] <= end <= newInterval[1] or start <= newInterval[0] <= end or start <= newInterval[0] <= end:
                newInterval[0] = min(start, newInterval[0]) 
                newInterval[1] = max(end, newInterval[1])
                continue
            else:
                if newInterval[1] < start and newInterval[0] != -1:
                    res.append(newInterval)
                    newInterval = [-1, -1]
                res.append((start, end))
        if newInterval[0] != -1:
            res.append(newInterval)
        return res
            
```