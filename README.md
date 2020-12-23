# how-to-algorithms

# class (data) type
| type        | classes |
| ----------- | ----------- |
| immutable   | int, float, decimal, complex, bool, str, tuple, range, frozenset, bytes |
| mutable     | list, dict, set, bytearray, user-defined classes (unless specifically made immutable) | 


### copy() vs deepcopy()
A shallow copy constructs a new compound object and then (to the extent possible) **inserts references** into it to the objects found in the original.
A deep copy constructs a new compound object and then, **recursively, inserts copies** into it of the objects found in the original.
```python

import copy
y = copy.copy(x)
y = copy.deepcopy(x)

```

### remove an element
```python

fruits = ['apple', 'pear', 'banana', 'orange']
fruits.remove('apple')  # remove removes the first matching value, not a specific index
del fruits[0]           # del removes the item at a specific index
fru = fruits.pop(0)     # pop removes the item at a specific index and returns it

# del and pop can be used for dict
del d[key]
value = d.pop(key)
```

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

### queue

```python
class MyQueue: 
    def __init__(self):  # First in first out.
        self.queue = []

    def push(self, x: int) -> None:  # Push element x to the back of queue.
        self.queue.append(x)

    def pop(self) -> int:  # Removes the element from in front of queue and returns that element.
        return self.queue.pop(0)

    def peek(self) -> int:   # Get the front element.
        return self.queue[0]

    def empty(self) -> bool:  # Returns whether the queue is empty.
        return len(self.queue) == 0
```


### stack
```python
class MyStack:
    def __init__(self):   # First in last out.
        self.stack = []

    def push(self, x: int) -> None:
        self.stack.append(x)

    def pop(self) -> int:  # Removes the element on top of the stack and returns that element.
        return self.stack.pop(-1)

    def top(self) -> int:   # Get the top element.
        return self.stack[-1]

    def empty(self) -> bool:   #
        return len(self.stack) == 0
```
