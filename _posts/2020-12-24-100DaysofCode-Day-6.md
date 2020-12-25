---
title: "#100DaysOfCode Day 6"
date: 2020-12-24
categories:
  - 100 Days of code
tags:
  - python
  - 100DaysOfCode
  - python crash course
  - Django
---

A bit more on classes today.  Then some file reading. 

```python
file_name = "dead_parrot.txt"
with open(file_name) as f:
    lines = f.readlines()

new_string = ""
for line in lines:
    new_string += line.rstrip()

print(f"{new_string}")

python file_read.py
Dead Parrot SketchThe cast:MR. PRALINEJohn CleeseSHOP OWNERMichael Palin--------------------------------------------------------------------------------The sketch:A customer enters a pet shop.Mr. 
Praline: Ello, I wish to register a complaint.
***snip***
```
And try/except/else for error catching:
```python
file_name = "file_is_not_here.txt"
try:
    with open(file_name) as f:
        lines = f.readlines()

    new_string = ''
    for line in lines:
        new_string +=line.rstrip()
except FileNotFoundError:
    print(f"Sorry, cannot find file named {file_name}")

else:
    print(new_string) #if file is found, this prints

python .\try_to_catch.py
Sorry, cannot find file named file_is_not_here.txt
```

A bit more on the [Django Tutorials][Django] as well.


[Django]:https://docs.djangoproject.com/en/3.1/intro/tutorial02/