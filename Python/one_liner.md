# One-Liner

### Swap two variables
```python
>>> a = 5
>>> b = 6
>>> a, b = b, a
>>> print(a, b)
6 5
>>>
```

### List comprehension
```python
>>> sqr = []
>>> for i in range(10):
...     sqr.append(i*i)
...
>>> print(sqr)
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>>> sqr = [i*i for i in range(10)]
>>> print(sqr)
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

```python
>>> sqr = []
>>> for i in range(10):
        if i % 2 == 0:
...         sqr.append(i*i)
...
>>> print(sqr)
[0, 4, 16, 36, 64]
>>> sqr = [i*i for i in range(10) if i % 2 == 0]
>>> print(sqr)
[0, 4, 16, 36, 64]
```

### if-else (ternary operator)
```python
>>> var = 42 if 3>2 else 99
>>> print(var)
42
```

### print only elements from a list in one line
```python
>>> data = [0,1,2,3,4,5]
>>> print(*data)
0 1 2 3 4 5
```

### days left in year
```console
$ python -c "import datetime; print((datetime.date(2022,12,31)-datetime.date.today()).days)"
8
```

### Reverse a List
```python
>>> data = [0,1,2,3,4,5]
>>> data = data[::-1]
>>> print(data)
[5, 4, 3, 2, 1, 0]
>>>
>>> palindrome = 'level'
>>> palindrome = palindrome[::-1]
>>> print(palindrome)
level
>>>
>>> print(palindrome == palindrome[::-1])
True
>>>
```

### Multiple variable assignments
```python
>>> name, age, lang = "John", 43, "Python"
>>> print(name, age, lang)
John 43 Python
```

## number string to integer list
```python
>>> user_input = "1 2 3 4 5"
>>> print(user_input.split())
['1', '2', '3', '4', '5']
>>> print(list(map(int,user_input.split())))
[1, 2, 3, 4, 5]
```

### Read file (multiple lines with leading space) into list
```python
names = [line.strip() for line in open("input.txt", "r")]
print(names)
```

### HTTP server
```console
$ python -m http.server
```

### Count of list item in another list
```python
>>> list1 = [ 3, 4, 7 ]
>>> list2 = [ 1, 2, 3, 4, 5, 6, 7, 4, 5, 6, 7 ]
>>> sum(x in list1 for x in list2)
5
>>>
```
### Hello World (easter egg)
```console
$ python -m __hello__ '__hello__.main()'
Hello world!

```

