# Binary Search

## TL;DR
Search on answer space using monotonic condition

```java
while (low <= high) {
    mid = low + (high - low) / 2;

    if (condition(mid)) {
        // answer can be here or on left
        high = mid - 1;
    } else {
        // answer is on right
        low = mid + 1;
    }
}
```

## When to use
- Sorted array
- Answer lies in range
- Min/Max problem

## Intuition
We are eliminating half space, not searching values

## Variants
- Lower bound
- Upper bound
- First true

## Mistakes
- Infinite loop (low = mid)
- Wrong condition

## Recognition
If problem says:
- minimum possible
- maximize value
→ binary search on answer

## Minimum valid answer problems

```python
while left < right:
    mid = (left + right) // 2
    if isValid(mid):
        right = mid
    else:
        left = mid + 1
    return left
```

## Exact match problem
```python
while left <= right:
    mid = (left + right) // 2
    if nums[mid] == target:
        return mid
    elif nums[mid] < target:
        left = mid + 1
    else:
        right = mid - 1
```
