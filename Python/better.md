# Notes for BETTER Python

### Use built-in function instead of using for-loop)
```python
>>> num = [10,20,30,40]
>>> print(sum(num))
100
```

### Use enumerate() to print index
```python
>>> num = [10,20,30,40]
>>> for i,v in enumerate(num, start=1):
...     print(i,v)
...
1 10
2 20
3 30
4 40
```

### Use zip() for multiple lists
```python
>>> num = [10,20,30,40]
>>> alist = ["a", "b", "c"]
>>> for v1,v2 in zip(num,alist):
...     print(v1, v2)
...
10 a
20 b
30 c
```

### Lazy generator
```python
>>> events = [('learn',5), ('learn',10), ('relax',20)]
>>> min = 0
>>> for event in events:
...     if event[0] == 'learn':
...         min += event[1]
...
>>> print(min)
15
>>>
>>> study = (event[1] for event in events if event[0] == 'learn')
>>> min2 = sum(study)
>>> print(min2)
15
>>>
>>> min3 = sum(study)
>>> print(min3)
0
```

### Use itertools()
```python
>>> lines = ['line1', 'line2', 'line3', 'line4', 'line5', 'line6', 'line7' ]
>>> for i, line in enumerate(lines):
...     if i >= 5:
...         break
...     print(line)
...
line1
line2
line3
line4
line5
>>> from itertools import islice
>>> ff_lines = islice(lines, 3)
>>> for line in ff_lines:
...     print(line)
...
line1
line2
line3
```

### Use of list comprehension
```python
>>> numbers = [1, 2, 3, 4, 5]
>>> result = [number for number in numbers if number % 2 == 0]
>>> result
[2, 4]
>>>
```

### Use Counter class to count
```python
>>> from collections import Counter
>>> words = ["apple", "banana", "cherry", "apple", "banana", "cherry"]
>>> counts = Counter(words)
>>> print(counts)
Counter({'apple': 2, 'banana': 2, 'cherry': 2})
```

### Use the any() and all() functions
```python 
>>> numbers = [1, 2, 3, 4, 5]
>>> result = any(number % 2 == 0 for number in numbers)
>>> print(result)
True
>>> result = all(number % 2 == 0 for number in numbers)
>>> result
False
>>>
```

### Use of with statement
```python
with open("file.txt") as f:
    data = f.read()
    
```

### Use of try-except-else-finally 
```python
>>> a, b = 1,0
>>>
>>> try:
...     print(a/b)
... except ZeroDivisionError:
...     print('division by zero')
... else:
...     print('no exception raised')
... finally:
...     print('Run this always')
...
division by zero
Run this always
>>> 
```

### Use of any(), all(), containment check
The  two statements are equivalent in Python:
```python
>>> all_match = all(condition(x) for x in iterable)
>>> all_match = not any(not condition(x) for x in iterable)
```
Same, these two statements are equivalent as well:
```python
>>> any_match = any(condition(x) for x in iterable)
>>> any_match = not all(not condition(x) for x in iterable)
```

```python
>>> numbers = [2, 1, 3, 4, 7, 11]
>>> has_five = any(n == 5 for n in numbers)
>>>
>>> numbers = [2, 1, 3, 4, 7, 11]
>>> has_five = 5 in numbers
>>> 
```
```python
>>> alist = [ 2, 4, 6, 8 ]
>>> blist = [ 2, 4, 6, 9 ]
>>>
>>> all_even = all( (n % 2) == 0 for n in alist )
>>> all_even
True
>>> all_even = all( (n % 2) == 0 for n in blist )
>>> all_even
False
>>> any_odd = any( (n % 2) == 1 for n in alist )
>>> any_odd
False
>>> any_odd = any( (n % 2) == 1 for n in blist )
>>> any_odd
True
```
