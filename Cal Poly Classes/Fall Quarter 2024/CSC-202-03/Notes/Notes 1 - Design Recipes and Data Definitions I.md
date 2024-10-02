9/25/2024

[Slideshow Link](https://docs.google.com/presentation/d/1P5nzgg6Pv1MEu98gA2HkHl8tjCl6Lfh0bjVKAvoZxpE/edit#slide=id.g2c84190a0a1_0_158)

How to represent problems in code.
 - Use a structured approach
 - 1. Data Definitions
 - 2. Purpose Statement, Contract, Header
 - 3. Test Cases
 - 4. Templates
 - 5. Write the Body of the Function

**Data Definitions**
 - Informs on how to write our function (aliases, nested, etc)
 - Valid definition should lead to valid output

 Type Alias - goal is clarity of function
```
from typing import TypeAlias
Age: TypeAlias = int
Name: TypeAlias = str
GPA: TypeAlias = float
Salary: TypeAlias = float
Roster:: TypeAlias = list[Name]

My_salary: Salary = 10000.00
My_gpa: GPA = 4.0
```

Compound Data Types
```
from typing import TypeAlias
income: TypeAlias = float
@dataclass
class Person:
name: str
age: int
salary: income
```

Mixed Data Types - more representation several datatypes
```
Number or String: TypeAlias = int | str
#Example usage
value1: NumberOrString = 42
value: NumberOrString "Hello"
```
- Sum Type - a type that allows multiple types, types optional
- Product Type - a type that combines multiple into one, requires types

Self referential Data Types
```
@dataclass
class Slide:
	title: str
	content: str
	Previous: Slide | None = None
	next: Slide | None = None
```
 - Recursive defined in terms of themselves
 - Foundation of recursion

**Purpose Statement, Contract, Header**
 - Purpose Statement = readability
 - Contract = inputs, outputs, conditions (pre/post)
 - Header = Dummy Body, Function Definition, detailing types of inputs and outputs
 
 Examples
 - Description
```
 #Calculates the average GPA of all students in a classroom
```
  - Parameters etc
```
  **

“”” Parameters:

    - classroom (Classroom): A Classroom object containing a list of Students.

    Returns:

    - float: The average GPA of students with a defined GPA. Returns 0.0 if no students have a GPA defined or the list is empty.

  

    Preconditions:

    - The classroom must not be None and should contain a list of Student objects.

    - Student GPA can be a float or None, where None indicates the GPA is not defined.

  

    Postconditions:

    - The function returns a non-negative float value representing the average GPA.”””

**
```

- Header
```
def function_name(parameter : type) -> type:
	pass or ... (tells python I know it's incomplete)
	# Docstring
	body
	return

def calculate_class_average_gpa(classroom : Classroom) -> float:
	pass
```

 - All together like this
```
 **

def calculate_class_average_gpa(classroom: Classroom) -> float:

    """

    Calculates the average GPA of all students in the classroom.

  

    Parameters:

    - classroom (Classroom): A Classroom object containing a list of Students.

  

    Returns:

    - float: The average GPA of students with a defined GPA. Returns 0.0 if no students have a GPA defined or the list is empty.

  

    Preconditions:

    - The classroom must not be None and should contain a list of Student objects.

    - Student GPA can be a float or None, where None indicates the GPA is not defined.

  

    Postconditions:

    - The function returns a non-negative float value representing the average GPA.

    """

  
**
```
