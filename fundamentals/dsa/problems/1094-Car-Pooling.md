# 1094. Car Pooling

**Intution:**
- Sort trips on from kms
- maintain heapInCar (to, peoples)
- maintain inCar count
- drop people at there kms 
- pick new people at kms 
- if anytime inCar people > capacity return False

**Mistake**
- for loop would have been enough
    
**MyCode**
- first try submitted XD
```python
class Solution:
    def carPooling(self, trips: List[List[int]], capacity: int) -> bool:
        # Check if any passenger is going from east to west 

        # Sort based on starting position
        trips = sorted([[frm, to, count] for count, frm, to in trips]) # (from, to, people)

        heapInCar = [] #(to, people)

        inCar = 0
        idx = 0
        n = len(trips)
        kms = 0
        while idx < n:
            trip = trips[idx]
            kms = trip[0]
            while heapInCar and kms >= heapInCar[0][0]:
                endTrip = heapq.heappop(heapInCar)
                inCar -= endTrip[1]
            if trip[2] + inCar > capacity:
                return False
            inCar += trip[2]
            heapq.heappush(heapInCar, [trip[1], trip[2]])
            idx += 1

        return True
```