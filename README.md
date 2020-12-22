# how-to-algorithms

### binary search
```python
left = 0
right = len(nums)-1
mid = (left + right) // 2

while left <= right:
    if nums[mid] == target:
        break
    elif nums[mid] > target:
        right = mid - 1
        mid = (left + right) // 2
    elif nums[mid] < target:
        left = mid + 1
        mid = (left + right) // 2
        
```
