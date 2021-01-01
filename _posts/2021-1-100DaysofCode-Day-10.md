---
title: "#100DaysOfCode Day 9"
date: 2020-12-29
categories:
  - 100 Days of code
tags:
  - python
  - 100DaysOfCode
  - postman
  
---

So, missed two days in a row.  Holiday season was tough.  Not sure if I'm supposed to "start over" or keep going in terms of the "challenge."  So, for now, keeping going, but maybe I'll disqualify myself later. ;)

Today was different.  I decided to look into the [Arrive Api][arrive-api] which is from a company called Parkwhiz.  Parkwhiz is also an application that my local ski resort uses to issue parking passes this season due to Covid-19 restrictions.  I thought this could be a personal project with some practical applications.  I'd like to query for available passes and then reserve a space if a day I want "opens up" (when people cancel, passes become available but are grabbed up quickly).

I downloaded Postman and started playing with queries.

```json
http://api.parkwhiz.com/v4/venues/478498

{
    "id": 478498,
    "name": "Mt. Bachelor Ski Resort",
    "address1": "13000 SW Century Dr",
    "city": "Bend",
    "state": "OR",
    "postal_code": "97703"
}
```
So, that's pretty neat.  Started struggling with actual queries for available spaces, however, due to some date/time formatting issues.  I apparently really need to understand some of ISO-8601 a bit better.  Found [this page][this-page] with some a good overview and some notes.   Still no joy on my queries, yet.

Once I get those queries working, I'll be using requests in Python and go from there.

[100DaysOfCode]:https://www.100daysofcode.com/faq/
[arrive-api]: https://developer.arrive.com/getting_started/#scopes
[this-page]:https://karinavarela.me/2019/06/07/iso-8601-time-standard/