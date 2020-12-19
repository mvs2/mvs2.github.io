---
title: "#100DaysOfCode Day 1"
date: 2020-19-20
categories:
  - 100 Days of code
tags:
  - python
  - 100DaysOfCode
  - python crash course
---

As I practice with this blog, I also intend to (re)start doing an hour of code.  This is at minimum my 3rd attempt to do this.  Starting this during the holiday season is a bit risky, but I'm determined to do it.  I'll both blog to summarize, and per the rules I'll start using my dormant twitter account (I mainly use twitter to read and learn from others).

I've been re-reading "Python Crash Course" by Eric Matthes.  I find it to be my personal favorite out of all the introductory Python texts out there.  

Today I focused on working with list slicing and remembering how list comprehensions work.

```python
 new_list = []
  for x in range(1,10):
    new_list.append(x+2)

  new_list
  [3, 4, 5, 6, 7, 8, 9, 10, 11] 
```
Versus:

```python
new_comp = [x+2 for x in range(1,10)]

new_comp
[3, 4, 5, 6, 7, 8, 9, 10, 11]
```
Also, with dictionaries, using "get()" in order to avoid errors dealing with a key not existing.

```python
vm_info = {'name':'ausvm01','cpu':'4','memory':'32GB','disk_count':'2'}

vm_info.get('name')
'ausvm01'

vm_info.get('vmname','Value does not exist')
'Value does not exist'
```
And a bit of simple looping through dictionaries:

```python
 for key in vm_info.keys():
	print(f'Key is: {key}')

	
Key is: name
Key is: cpu
Key is: memory
Key is: disk_count
```