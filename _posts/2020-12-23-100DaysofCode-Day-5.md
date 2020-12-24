---
title: "#100DaysOfCode Day 4"
date: 2020-12-23
categories:
  - 100 Days of code
tags:
  - python
  - 100DaysOfCode
  - python crash course
  - Django
---

Some more on functions, specifically passing arbitrary numbers of arguments.

```python
def print_it_all(*stuff_to_print): #the * allows multiple arguments to be passed
    for everything in stuff_to_print:
        print(everything)


print_it_all("Hi")

print_it_all("Greetings!", "good-bye", "test")

python arb_args.py
Hi
Greetings!
good-bye
test
```
Also did some reading on classes.
```python
class Fruit:
    """Oversimplification for learning purposes."""

    def __init__(self, name, color, juciness):
        self.name = name
        self.color = color
        self.juciness = juciness
    
    def eat(self):
        """fun times"""
        print(f"Hope you're enjoing this {self.name}")
    
    def check_ripeness(self):
        """can't eat if over or under-ripe"""
        print(f"This {self.name} is ready to eat!")
        return "Ready"

"""for testing purposes acting on the class w/in same file"""

my_apple = Fruit("apple", "red", "Very")
to_eat = my_apple.check_ripeness()
if to_eat == "Ready":
    print(f"Oh boy, time to eat the {my_apple.name}")
my_apple.eat()

python fruit_2.py
This apple is ready to eat!
Oh boy, time to eat the apple
Hope you\'re enjoing this apple
```
And now for a child class that inherits from the parent class.

```python
class Fruit:
    """Oversimplification for learning purposes."""

    def __init__(self, name, color, juciness):
        self.name = name
        self.color = color
        self.juciness = juciness
    
    def eat(self):
        """fun times"""
        print(f"Hope you're enjoing this {self.name}")
    
    def check_ripeness(self):
        """can't eat if over or under-ripe"""
        print(f"This {self.name} is ready to eat!")
        return "Ready"

class Banana(Fruit):
    """Now a sublcass of Fruit"""
    def __init__(self, name, color, juciness):
        super().__init__(name, color, juciness)
    
    def peel(self):
        print(f"You peeled it!  Ready to eat")

my_b = Banana("Banana", "Yellow", "Dry")
my_b.peel()
my_b.eat()
```

Some work on the  [Django Tutorials][Django] also, but not as much as I would have liked today.
OK, another day down.  Yay!

[pycheckio]:https://py.checkio.org/
[Django]:https://docs.djangoproject.com/en/3.1/intro/tutorial02/