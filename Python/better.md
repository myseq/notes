# Tips for BETTER Python

### Use built-in function instead of using for-loop)
```python
>>> num = [10,20,30,40]
>>> print(sum(num))
100
```

### Use enumerate to print index
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



