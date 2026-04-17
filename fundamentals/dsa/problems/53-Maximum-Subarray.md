# 53. Maximum Subarray

# Intution
- Maintain high till now
- update high if max(num, high + num) 
  - **Continous array will only make sense if it is incresing after adding the current index nums[i]**
  - **If Continous part is smaller than current nums[i] then it is useless to continue with continous array**
  - **so we should start new continous array from current point**
- update res = max(res, high)

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        res = nums[0]
        high = nums[0]
        for num in nums[1:]:
            high = max(num, high + num)
            res = max(res, high)
        return res

```
**Topics**
[[Kadanes-Algorithm]]