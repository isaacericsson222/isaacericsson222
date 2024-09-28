9/25/2024
[Set 1](https://canvas.calpoly.edu/courses/137532/assignments/1102901)

1.
```
from dataclasses import dataclass

@dataclass
class Person
	name: str
	age: int
	grades: list[float]
```

2.
```
from typing import TypeAlias

ListOfFloats: TypeAlias = list[float]
```

3.
```
list1: list[]
findNum: int

def contains_value (list1 : findNum) -> int:
	return findNum in list1

```

4.
```
def test_find_midpoint_element(self):
	
```

5.
```
from dataclasses import dataclass

@dataclass
class Library
	Book: str
	Patron: str
	time: TypeAlias = int
	Loan: time
	Card: Patron
	
```

6.
```
def test_list_sort_raise_type_error(self):
	with self.assertRaises(TypeError):
		acceptList(98)
```

7.
```
def reverse_string(str1) -> str
	return str1[::-1]
```

8.
```
from dataclasses import dataclass

@dataclass
class Car:
	mpg: int # Miles per gallon
	year: int # Year of manufacture
	model: str # Model of the car
	owner: str # Owner's name
	weight: int # Weight of the car in pounds
```

9.
```
from __future__ import annotations

FutureType: TypeAlias = "newVar | None"
newVar: TypeAlias = int
```

10.
```
from dataclasses import dataclass
from typing import TypeAlias

@dataclass
class Robot:
	Point: TypeAlias = tuple[int,int]
	Point = (0, 0)
```