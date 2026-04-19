# Python 

### 1. Syntex 
**1. Converts into other type**

```python
num = 10
str(num) # Converts number type into string type

num_string = "10"
int(num_string) # Converts string type into int type
```

**2. Heap**
- **Note: Heap is min heap**
- To process max heap you can add all numbers with Negative(-ve) sign, and to get original do num * (-1).
  
```python
heap = [1, 2, 3, 4, 5]
heapq.heapify(heap)
heapq.heappop(heap)
heapq.heappush(heap, 6)
 
heapq.heappush(heap, (first_value, second_value)) # Sorting will be on first value
heappushpop(heap, item) #Pushes a new item and then pops the smallest
heapreplace(heap, item) #Pops the smallest item first, then pushes the new item.
nlargest(n, iterable) or nsmallest(n, iterable) #Returns the top largest or smallest elements
```

**3. Math functions**
```python
import math

num = 25
math.sqrt(num) # 5
math.pow(num, 2) # 625
```

**4. Counter**
- Create a map from list of elements with freq count map
```python
from collections import Counter
c = Counter(['a', 'b', 'a', 'c', 'b', 'a']) # {"a":3, "b":2, "c":1}
for element, count in c.items():
    print(element, count)
```

**5. Default Dict**
- Automatically provides a default value for any key that does not exist, preventing KeyError exceptions.
```python
from collections import defaultdict
counts = defaultdict(int)
counts['apple'] += 1  # No error; 'apple' starts at 0, then becomes 1

groups = defaultdict(list)
groups['fruits'].append('apple') # No error; 'fruits' starts as []
```

**6. List**
```python
nums = [1, 2, 3, 4, 5]
nums.remove(5) # nums = [1, 2, 3, 4]
```

**7. Set**
```python
nums = list(set(nums1) - set(nums2)) # Get distinct nums (all num not present in nums2)
```

**8. Sorting**
**Note:** Sorting done on first value by default
```python
    tasks = sorted([(first, second, i) for i, (first, second) in enumerate(tasks)])
```

**9. Find Index of max element**
```python
maxRoomId = 0
for i, count in enumerate(rooms):
    if count > rooms[maxRoomId]:
        maxRoomId = i

rooms.index(max(rooms))
```

**10. Shorthand for If else condition**
```python
if num > 0:
    return num
else:
    return num2

return num if num > 0 else num2
```

**11. Queue**
```python
q = deque()
q.append(i)
q.popleft()
```