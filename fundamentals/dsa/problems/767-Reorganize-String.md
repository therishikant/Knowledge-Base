# 767. Reorganize String

**Intution:** 
- Use freq and maxHeap to get max freq element each time
- Maintain previous for last appended character

# Mistake:
- Forget to set None to previous if count == 0
- Added res = res + previous[1], not needed
- forget to add freq.items() while itrating over freq

```python
class Solution:
    def reorganizeString(self, s: str) -> str:
        
        freq = Counter(s)
        heap = [(-f, s) for s, f in freq.items()]

        heapq.heapify(heap)
        res = ""
        previous = None
        while heap:
            top = heapq.heappop(heap)
            res = res + top[1]
            if previous:
                if previous[0] == 0:
                    previous = None
                else:
                    heapq.heappush(heap, previous)
            previous = (top[0] + 1, top[1])
        if previous and previous[0] != 0:
            return ""
        return res
```