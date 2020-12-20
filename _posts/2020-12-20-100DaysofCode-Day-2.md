---
title: "#100DaysOfCode Day 2"
date: 2020-12-20
categories:
  - 100 Days of code
tags:
  - python
  - 100DaysOfCode
  - python crash course
---

Today dealt more with dictionaries, setsf for lists, and nesting dictionaries and lists within dictionaries.

I found "sets" interesting and something I must have forgotten. According to ["Python Crash Course"][python-crash-course]* "A set is a collection in which each item must be unique.... When you wrap set() around a list that contains duplicate items, Python identifies the unique items in the list and builds a set from those items."


```python
sandwich_orders = {'jerry': 'salami', 'marcus': 'veggie', 'susan': 'veggie', 'larry': 'grilled cheese'}

sandwich_orders.values()
dict_values(['salami', 'veggie', 'veggie', 'grilled cheese'])

set(sandwich_orders.values())
{'salami', 'grilled cheese', 'veggie'}
```

Some playing with nested dictionaries/lists:

```python
food_orders = {
	'jerry': {'sandwich':['salami','grilled cheese'],'drink':'sprite'},
	'marcus':{'sandwich':[ 'veggie'],'drink':'diet coke'},
	'susan':{'sandwich':['veggie','hummus'],'drink':'water'},
	'larry':{'sandwich':['grilled ham'],'drink':'fanta'},
	}

for person,order in food_orders.items():
	print(f'{person.title()} wants to eat:')
	for sw_type in order['sandwich']:
		print(f'\t{sw_type}')
	print(f'\tAnd {order["drink"].title()} to drink')

  Jerry wants to eat:
	salami
	grilled cheese
	And Sprite to drink
Marcus wants to eat:
	veggie
	And Diet Coke to drink
Susan wants to eat:
	veggie
	hummus
	And Water to drink
Larry wants to eat:
	grilled ham
	And Fanta to drink

```

*While I am re-working my way quickly through this book, I should point out I get no monetary compensation (I don't do ads/affiliate links) from recommending it.  There are other very good books, too, I just happen to like the breadth this one covers.  I'm also reading Al Sweigart's latest, but Python Crash Course is currently taking priority.

[python-crash-course]: https://nostarch.com/pythoncrashcourse2e
[100DaysOfCode]:https://www.100daysofcode.com/