# Kadane's Algorithm
- Kadane's Algorithm is an efficient dynamic programming technique used to find the maximum sum of a contiguous subarray within a 1D array of numbers in O(n) time complexity.


```python
    res = nums[0]
    high = nums[0]
    for num in nums[1:]:
        high = max(num, high + num)
        res = max(res, high)
    return res
```

