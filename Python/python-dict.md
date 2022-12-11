# Python Dict()
Some of my quick notes on using Python Dict()
- unordered
- changeable 
- index
- no-dup

```python
this_dict = { 'brand': 'find', 'model': 'mustang', 'year': '1964' }
x = this_dict['model']
x = this_dict.get('model')
this_dict['year'] = '2018'
```

### Dictionary Comprehension
```python

```

### To get key by value in Dict()
```python
print( [ k for k,v in a.items() if v==b ] )
```
```python
mydict = { 'george': 16, 'amber': 19 }
print(list(mydict.keys())[list(mydict.values()).index(16)])
# george
```

### Sorting Dictionary
```python
>>> people = {3: "Jim", 2: "Jack", 4: "Jane", 1: "Jill"}

>>> # Sort by key
>>> dict(sorted(people.items()))
{1: 'Jill', 2: 'Jack', 3: 'Jim', 4: 'Jane'}

>>> # Sort by value
>>> dict(sorted(people.items(), key=lambda item: item[1]))
{2: 'Jack', 4: 'Jane', 1: 'Jill', 3: 'Jim'}
```
