# 2402. Meeting Rooms III

**Intution**
- Track used, avalible rooms through heap
- Use room list to track meeting count
- iterate through meetings 
- free up used room if start time of meeting greater than used meeting end time
- if no room is free free up nearest used room
- allocate current meeting in availabe room
- rooms.index(max(rooms))

**Mistake**
- not able to code 
- not thing in currect optimise way so that coding is easy 

**New Learning : Same output**
```python
maxRoomId = 0
for i, count in enumerate(rooms):
    if count > rooms[maxRoomId]:
        maxRoomId = i

rooms.index(max(rooms))
```


```python
class Solution:
    def mostBooked(self, n: int, meetings: List[List[int]]) -> int:
        meetings.sort()
        free = [i for i in range(n)]
        heapq.heapify(free)
        used = [] # [endTime, roomId]
        rooms = [0] * n
        for start, end in meetings:
            while used and used[0][0] <= start:
                _, room = heapq.heappop(used)
                heapq.heappush(free, room)
            
            if not free:
                end_time, room = heapq.heappop(used)
                end = end_time + (end - start)
                heapq.heappush(free, room)
            
            room = heapq.heappop(free)
            heapq.heappush(used, (end, room))
            rooms[room] += 1
        return rooms.index(max(rooms))
```