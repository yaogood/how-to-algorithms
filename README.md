# how-to-algorithms

### sort
```python
list_a.sort()            # build-in sorting, list_a is changed
list_b = sorted(list_a)  # list_a is unchanged

list_c = sorted(list_a, reverse=True, key=lambda element_class: element_class.variable)

# element_class is the class name of elements in list_a
# if reverse is True, then descending


from operator import itemgetter, attrgetter
def multisort(xs, specs):
    for key, reverse in reversed(specs):  # The reversed() function returns the reversed iterator of the given sequence.
        xs.sort(key=attrgetter(key), reverse=reverse)
    return xs
    
multisort(list(student_objects), (('grade', True), ('age', False)))

```

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
