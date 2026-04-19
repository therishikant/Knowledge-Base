# 55. Jump Game

**Intution**
- start from index-n
- move index-n to index-i if able to reach end position
- at last if index-n == index-0 return True

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        end = len(nums) -1
        for i in range(len(nums) - 1, -1, -1):
            if i + nums[i] >= end:
                end = i
        
        return True if end == 0 else False
```

**Topics**
- [[dp]]
- [[greedy]]