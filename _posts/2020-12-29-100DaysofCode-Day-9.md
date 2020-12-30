---
title: "#100DaysOfCode Day 9"
date: 2020-12-29
categories:
  - 100 Days of code
tags:
  - python
  - 100DaysOfCode
  - pycheck.io
  - Django
---

Some Django modeling practice which involved setting up a new project.  Then setting up a new app under that project.  Then creating some simple models (in this case, "Pizza" and "Topping").  Then migrating the new models and adding them to the admin interface.

```python
from .models import Pizza, Topping


admin.site.register(Pizza)
admin.site.register(Topping)
```




Also solved a [py.checkio.org][pycheckio] exercise that dealt with removing everything prior to a certain index in a list.

[100DaysOfCode]:https://www.100daysofcode.com/faq/
[python-crash-course]: https://nostarch.com/pythoncrashcourse2e
[pycheckio]:https://py.checkio.org/