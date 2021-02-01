# how-to-algorithms

## data structure

##### 1. hash table
unordered dict, ordered dict
##### 2. linked list/array/string: 
KMP
##### 3. tree
binary search tree, trie, segment tree, 树状数组（Binary Indexed Tree）
##### 4. graph 
最小生成树（Prim, Kruskal）, 最短路径（BFS, DFS, Floyd, Dijkstra, Bellman-Ford, SPFA）, Topological Sort
##### 5. stack
##### 6. queue
##### 7. dequeue
##### 8. heap/priority queue


## algorithms

##### 1. sort: 
heap sort, merge sort, bucket sort (pigeonhole sort, counting sort), radix sort, quick sort, insert sort, selection sort, bubble sort
##### 2. binary search
##### 3. dynamic programming
##### greedy
##### breadth first search
##### depth first search
##### backtracing
##### recursion
##### divide and conquer
##### union find
##### bit manipulation
##### geometry
##### sampling
reservoir sampling, rejection sampling



### operators
```python
# -3 // 2 => -2
# int(-3/2) => -1
```

### basic
```python
# a better update dict method
dict[k] = dict.get(k, value) + 1  # if k in dict, then dict[k]=dict[k]+1, else new dict[k]=value+1
# value: Optional. A value to return if the specified key does not exist. Default value None.
```

### class (data) type
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

# Complex Sorts (recommended)
from operator import itemgetter, attrgetter
def multisort(xs, specs):
    for key, reverse in reversed(specs):  # The reversed() function returns the reversed iterator of the given sequence.
        xs.sort(key=attrgetter(key), reverse=reverse)
    return xs
multisort(list(student_objects), (('grade', True), ('age', False)))

# Decorate-Sort-Undecorate
decorated = [(student.grade, i, student) for i, student in enumerate(student_objects)]
decorated.sort()
res = [student for grade, i, student in decorated]

# cmp is not supported after python 3.x
# functools.cmp_to_key() and functools.total_ordering decorator is used in custom classes


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

### BFS
```python
queue = collections.deque()
queue.append(start_state)
while queue and some_conditions:
    length = len(queue)
    for i in range(length):
        cur_state = queue.popleft()
        # do some operations on current_state and generate next_states
        queue.append(next_state)
```

### DFS
```python

def dfs(cur, path_set_or_list):
    if final_state:
        # do some operations about results
        return results
    for next in dic[cur]:
        # do some operations
        dfs(next)
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
