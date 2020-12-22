---
title: "#100DaysOfCode Day 4"
date: 2020-12-22
categories:
  - 100 Days of code
tags:
  - python
  - 100DaysOfCode
  - python crash course
  - pycheck.io
  - Django
---

Today was some basic "functions" review.  I've written quite a few of those lately for work, so most of this I have down pretty well, thank goodness. Something I *didn't* recall immediately was that there's really not much reason to 'return' a list since lists are modified in place (if you change a list in the function it changes everywhere).

```python
def change_list(list_to_change):
    list_to_change.pop()  # pop the last element off of the list.
    # notice no 'return'


def main():
    my_list = ["cookies", "ice cream", "pumpkin pie"]
    print(f"my list is {my_list}")
    print("***************")
    change_list(my_list)
    print(f"Now my list is {my_list}")


if __name__ == "__main__":
    main()
```

Some more time on [py.checkio.org][pycheckio] today as well.  Was doing good, but it does generally require me to sometimes review Python Built in Types and their methods.  Today I learned about 'reversed' with a problem that is supposed to "find out how many zeros a given number has at the end."  I figured I had to convert the interger to a string (previous problems required this as well).  I wasn't quite sure how to 'slice' or split it up (it seems some other solutions used 'rsplit' so I'll review those as well).

Luckily, found an example solution using 'reversed' that aided me. Nice to know about that option.

```python
def end_zeros(num: int) -> int:
    my_string = str(num)
    count = 0
    for numstr in reversed(my_string):  # iterate through string in reverse order.
        if numstr == "0":
            count += 1
        else:
            return count
    return count
```

Note: The type hints in the function are provided by pycheckio.  I'm not fully used to type hints yet, but since they are provided, I just go with it. 

Also going to squeeze in some [Django][Django] tutorials as well today if possible.  I got a little bit done yesterday from the project in the Python Crash Course book.


[pycheckio]:https://py.checkio.org/
[Django]:https://www.djangoproject.com/