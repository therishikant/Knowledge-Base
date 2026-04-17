# 918. Maximum Sum Circular Subarray

**Intution**

- In a circular array, the maximum subarray can either be a normal one (no wrapping) or a wrapping one (end connects to beginning).

- For the normal case, we just use Kadane’s algorithm.

- For the wrapping case, we take the total sum of the array and subtract the minimum subarray sum (found using a modified Kadane’s). This works because removing the most negative part gives us the maximum possible wrapping sum.

- Finally, we return the maximum of the normal subarray and the wrapping subarray.

- If all numbers are negative, we simply return the largest element, since adding more elements would only decrease the sum.

```python
class Solution:
    def maxSubarraySumCircular(self, nums: List[int]) -> int:
        n = len(nums)
        globalMax, globalMin = nums[0], nums[0]
        curMax, curMin = 0, 0
        total = 0
        for num in nums:
            curMax = max(curMax + num, num)
            curMin = min(curMin + num, num)
            total += num
            globalMax = max(globalMax, curMax)
            globalMin = min(globalMin, curMin)
        
        return if globalMax > 0 else globalMax

```
**Topics**
- [[Kadanes-Algorithm]]
- [[greedy]]