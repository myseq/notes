# Types of Data Structure
There are 4 main types of data structures in Python:
1. List - ordered, changeable, allow-duplicate
2. Dictionary - unordered, changeable, index, no-dup
3. Tuple - ordered, unchangeable, allow-duplicate
4. Set - unordered, unindexed, no-dup


### Examples
```python
# main data structure
ppl_list = ["Jim", "Jack", "Jane", "Jill"]
ppl_dist = {3: "Jim", 2: "Jack", 4: "Jane", 1: "Jill"}
ppl_tuple = (  'apple', 'banana', 'cherry'  )
ppl_set = { 'apple', 'banana', 'cherry' }

# mix of data structure
list_dict_ppl = [  
   {"id": 3, "name": "Jim"}, 
   {"id": 2, "name": "Jack"}, 
   {"id": 4, "name": "Jane"},  
   {"id": 1, "name": "Jill"}   ]
   
list_tuple_ppl = [ 
    (3, "Jim"),  
    (2, "Jack"), 
    (4, "Jane"), 
    (1, "Jill")    ]

```
