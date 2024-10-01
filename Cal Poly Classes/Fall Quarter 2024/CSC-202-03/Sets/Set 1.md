9/25/2024
[Set 1](https://canvas.calpoly.edu/courses/137532/assignments/1102901)

1.
```
	from dataclasses import dataclass
	
	@dataclass
	class Person:
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
def find_midpoint_element(numbList: list[int]):
	pass

def test_find_midpoint_element_correct_response(self):
	list1 = [1,2,3,4,5]
	self.assertEqual(find_midpoint_element(list1), 3, "Should be 3")
```

5.
```
from dataclasses import dataclass
from typing import TypeAlias

@dataclass
class Library:
Book: str
Patron: str
time: TypeAlias = int
Loan: time

#Methods that operate on these data structures
#def overdue_books(Book, loan):
#pass (will tell if a book is overdue)
```

6.
```
def test_list_sort_raise_type_error(self):
	with self.assertRaises(TypeError):
		acceptList(98)
```

7.
```
def reverse_string(str1) -> str:
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