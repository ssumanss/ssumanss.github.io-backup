---
layout: post
title:  "Namedtuple in Python"
date:   2018-11-07
categories: jekyll update
author: ssuman
excerpt_separator: "<!--more-->"
published: true
---

Python supports the type of container like dictionary is called `namedtuple` is present in module `collection`. It looks like a tuple with each index has a name, and this enable us to iterate it from any index from a list of namedtuple. Another way to think it as a object with no particular method associated with it.
<!--more-->

## Creating a namedtuple

Suppose we want to make a list of students with distinct name, age and score. First we try the to write is as a simple tuple

```python
student1 = ("Ram", 23, 67)
student2 = ("Shyam", 24, 76)
```

 In order to give the students a specific structure,  we will define a namedtuple of student.

 ```python
# Step 1: import namedtuple from collections
from collections import namedtuple
# Step 2: define a prototype of student
Student = namedtuple('Student', ["name", "age", "marks"])
Student = namedtuple('Student', 'name age marks') # alternative
# Step 3: define each individual students 
student1 = Student("Ram", 23, 67)
student2 = Student("shyam", 24, 76)
```
Thus we defined a namedtuple of specific type.

## Usage

Here we can see that we have done more work in defining two distnct students, so we can hope it can help us later in some way. Now we will learn how to use this in our program.

### Same as tuple

A namedtuple can do everything a tuple can do. Remember tuple is an immutable objects and each element can be accessed through an index.

```python
# In case of tuple 
>>> student1[0]
Ram
>>> student1[1]
23

# In case of namedtuple
>>> student1[0]
Ram
>>> student1[1]
23
```  

We can unpack values of namedtuple same as tuple.

```python
name1, age1, marks1 = student1
```

Namedtuple are also immutable, so we can't change the value of an entry once created.

```python 
>>> student1[1] = 25
AttributeError: can't set attribute
```

### Accessing by attribute and getattr
We can access the entries of namedtuple by keys is same as dictionary or we can use `getattr` function to get a value corresponding to a key.

```python 
>>> student1.name
Ram
>>> student1.age
23

# we can use getattr function to call same thing 
>>> getattr(student1, 'name')
Ram
>>> getattr(student1, 'age')
23
```

### Sorting with respect of any keys

Suppose we have a list of namedtuple of same type, like we have a list of students with name, age and marks. We can sort that list in using any key.

```python 
# Take a list of students
sequence = [student1, student2]
# sorting accroding to age
l = sorted(sequence, key=attrgetter('age'))
# sortng using lambda according to marks
l = sorted(squence, key=lambda x: x.marks)
# sorting using index require some work
from operator import itemgetter
l = sorted(sequance, key=itemgetter(0))
```
