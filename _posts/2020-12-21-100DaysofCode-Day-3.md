---
title: "#100DaysOfCode Day 3"
date: 2020-12-21
categories:
  - 100 Days of code
tags:
  - python
  - 100DaysOfCode
  - python crash course
  - pycheck.io
---

Today focused on some while loops with dictionaries, "continue," and using a while loop to remove items from a list.

```python
keep_going = True
prompt = "Please enter an exercise you performed yesterday."
prompt += "\nEnter 'quit' to exit the program.  "
exercises = []
while keep_going:
    performed = input(prompt)
    if performed.lower() == "quit":
        print("What a great day you had!  You did:")
        for exercise in exercises:
            print(f"{exercise}")
        print("Thank you, exiting program....")
        keep_going = False
    else:
        print(f"Adding {performed} to list")
        exercises.append(performed)


python while_prompts.py  
Please enter an exercise you performed yesterday.
Enter 'quit' to exit the program.  Sit-ups
Adding Sit-ups to list
Please enter an exercise you performed yesterday.
Enter 'quit' to exit the program.  Push-ups
Adding Push-ups to list
Please enter an exercise you performed yesterday.
Enter 'quit' to exit the program.  Hiking
Adding Hiking to list
Please enter an exercise you performed yesterday.
Enter 'quit' to exit the program.  quit
What a great day you had!  You did:
Sit-ups
Push-ups
Hiking
Thank you, exiting program....     

```

```python
results = {}
keep_going = True
while keep_going:
    name = input("\n Enter a name  ")
    color = input(f"What is {name.title()}'s favorite color? ")
    # store above in dictionary
    results[name] = color
    # give them chance to exit
    response = input("Would you like add another entry? (yes/no) ")
    if response.lower() == "no":
        keep_going = False

for name, color in results.items():
    print(f"{name.title()}'s favorite color is {color.title()}")


python .\dictionary_input.py

 Enter a name  marcus
What is Marcus's favorite color? Green
Would you like add another entry? (yes/no) yes

 Enter a name  Susan
What is Susan's favorite color? Red
Would you like add another entry? (yes/no) yes

 Enter a name  Larry
What is Larry's favorite color? purple
Would you like add another entry? (yes/no) no
Marcus's favorite color is Green
Susan's favorite color is Red   
Larry's favorite color is Purple
```
Using continue:

```python
my_list = ["apples", "bananas", "carrots", "ice cream", "cookies", "kale"]
while my_list:
    food = my_list.pop()
    # don't tell anyone about our unhealthy foods
    if food == "ice cream" or food == "cookies":
        continue
        # note that 'continue' returns us to the beginning of the loop
    else:
        print(f"You ate {food}!  What a healthy choice!")

python while_continue.py
You ate kale!  What a healthy choice!   
You ate carrots!  What a healthy choice!
You ate bananas!  What a healthy choice!
You ate apples!  What a healthy choice! 
```

Removing items from a list:

```python
cars = ["audi", "bmw", "VW", "Toyota", "Mercedes", "bmw", "datsun", "bmw", "lexus"]
print(cars)
print("Sorry, all BMW's have to go....")
while "bmw" in cars:
    cars.remove("bmw")
print(cars)

python remove_list_items.py
['audi', 'bmw', 'VW', 'Toyota', 'Mercedes', 'bmw', 'datsun', 'bmw', 'lexus']
Sorry, all BMW's have to go....
['audi', 'VW', 'Toyota', 'Mercedes', 'datsun', 'lexus']
```

I also spent some time on [py.checkio.org][pycheckio] doing some random exercises that involved strings and slicing.  Spent a bit too much time trying to get the 'local editor' option to work and failing (seems to not understand Win 10 directories).  Otherwise, completed two excercises and may do some more through out the day.


[pycheckio]:https://py.checkio.org/