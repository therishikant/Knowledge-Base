# 435. Non-overlapping Intervals

**Intution**
- Short all interval on start time
- Two interval are overlapping when start < prevEnd
- Or We should keep interval which has minimum end value becuase it has less chance of overlapping with another interval

**Mistake**
- Not able to think of optimal approch

**Code**
```python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        intervals.sort()
        prevEnd = intervals[0][1]
        res = 0
        for start, end in intervals[1:]:
            if start >= prevEnd:
                prevEnd = end
            else:
                res += 1
                prevEnd = min(end, prevEnd)
        return res 
```