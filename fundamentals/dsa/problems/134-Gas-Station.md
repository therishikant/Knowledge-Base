# 134. Gas Station

**Intution**
- if any point **total < 0** then we can't reach next position, and internally we will not be able to circle back 
- we will update res if total < 0
- Solution is garentee to be unique, If exist.
- Greedy solution 

**Code**
```python
class Solution:
    def canCompleteCircuit(self, gas: List[int], cost: List[int]) -> int:
        if sum(gas) < sum(cost):
            return -1
        
        total = 0
        res = 0

        for i in range(len(gas)):
            total += (gas[i] - cost[i])
            if total < 0:
                total = 0
                res = i + 1
            
        return res
```

**Topics**
[[greedy]]