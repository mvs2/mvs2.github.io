---
title: "#100DaysOfCode Day 7"
date: 2020-12-26
categories:
  - 100 Days of code
tags:
  - python
  - 100DaysOfCode
  - python crash course
  - Django
---

First off, yes, I skipped Dec. 25.  According to the ["rules,"][100DaysOfCode] one skipped day is OK.  Two is forbidden, apparently.  I expect I might miss New Year's Day as well.

Started getting into testing today. 

```python
"""accepts a city name and a country name.  returns single string"""


def city_co(city, country):
    new_string = f"{city.title()}, {country.title()}"
    return new_string

```
Saved as city_functions.py

```python
import unittest
from city_functions import city_co


class City_Country_Test(unittest.TestCase):
    def test_city_country(self):
        """does it work?"""
        formatted_string = city_co("santiago", "chile")
        self.assertEqual(formatted_string, "Santiago, Chile")

if __name__ == "__main__":
    unittest.main()

python test_cities.py
.
----------------------------------------------------------------------
Ran 1 test in 0.000s

OK
```

A slight modification:

```python

def city_co(city, country, population):
    if population:
        new_string = f"{city.title()}, {country.title()} population = {str(population)}"
    else:
        new_string = f"{city.title()}, {country.title()}"

    return new_string
```

Modified tests:
```python
class City_Country_Test(unittest.TestCase):
    def test_city_country_pop(self):
        """does it work?"""
        formatted_string = city_co("Santiago", "Chile", population=7000000)
        self.assertEqual(formatted_string, "Santiago, Chile population = 7000000")

        formatted_string = city_co("imadethisup", "pylandia", 1984)
        self.assertEqual(formatted_string, "Imadethisup, Pylandia population = 1984")


python test_cities_pop.py 
.
----------------------------------------------------------------------
Ran 1 test in 0.000s



```

No Django today. 
[100DaysOfCode]:https://www.100daysofcode.com/faq/