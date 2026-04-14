# 1405. Longest Happy String

**Intution:** 
- Use maxHeap to check for max count char
- append new heap top if len(res) > 1 and res[-1] == res[-2] == char
- else append heap Top 

**Mistake:**
- Not able to code completely 

```python
class Solution:
    def longestDiverseString(self, a: int, b: int, c: int) -> str:
        heap = []
        if a > 0:
            heap.append([-a, "a"])
        if b > 0:
            heap.append([-b, "b"])
        if c > 0:
            heap.append([-c, "c"])

        heapq.heapify(heap)
        previous = None #(-count, char)
        res = ""
        while heap:
            count, char = heapq.heappop(heap)
            if len(res) > 1 and res[-1] == res[-2] == char:
                if not heap:
                    break
                count2, char2 = heapq.heappop(heap)
                res += char2
                count2 += 1
                if count2:
                    heapq.heappush(heap, [count2, char2])
            else:
                res += char
                count += 1
            if count:
                heapq.heappush(heap, [count, char])
        
        return res
```

