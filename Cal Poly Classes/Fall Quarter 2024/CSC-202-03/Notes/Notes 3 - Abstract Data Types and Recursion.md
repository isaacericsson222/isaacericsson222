9/30/2024

[Slideshow Link](https://docs.google.com/presentation/d/1Lks-VClf0eUWPXbB8vhCmrkSldmtM-p6BZ71SzmmkD8/edit?usp=sharing)

Abstract Data Types (ADTs)
 - The theoretical model of which to build a data structure
 - Typically the operations are setting, getting, and deleting
 - Think of a list without syntax (.add etc) with just the ability to set, get, and delete

Implementing ATDs
 - Implemented using concrete data structures
 - In order to chose the best option consider it's size, properties, operations, frequency, and memory space available
 - What to choose, a list or a dictionary?

Recursion
 - An algorithm that calls upon itself until base case is reached in order to find a solution
 - Here is a recursive definition for factorial n! = n * (n - 1) * (n - 2) * (n - 3) * ... * 3 * 2 * 1
 - Factorial has the base case of n is 0 or 1 because we know and can easily solve for 0! or 1!
 - Factorial has the recursive case of return n * factorial(n - 1) which leads the function to repeat until 0 or 1 is reached
```
def factorial(n: int) -> int:
	#base case: if n is 0 or 1:

	if n in (0, 1):
		return 1

	# Recursive case: n * factorial of (n - 1)

	else:
		return n * factorial(n - 1)
```

Implementing Recursive Functions
 - Identify the base case
 - Ensure proper termination
 - Make sure recursive case progresses to base case
```
#convert to recursive
i = 0

while i < 11:
	i += i
return i
```

 - base case is i = 11
 - recursive case is i  += i
```
#converted

def sum (i = 0, target) -> int:
	if (i >= target):
		return i
	else:
		return sum(i + 1, target)

```

Recursive Linear Search
 - Call | Case | Return | Receive
```
def recursive_linear_search(arr: list[int], target: int, index: int = 0) -> bool:
	# base case 1: If the index of the array reaches the length of the array, the
	target is not found

	if index == len(arr):
		return False

	# base case 2: if target is found at the current index

	if arr[index] == target:
		return True

	# recursive case: move to next index

	return recursive_linear_search(arr, target, index + 1)
 
```

 - Whenever a recursive function is evoked, a stack element is created and pushed to the **top** of the call stack
 - After a full recursive process finishes, the stack is deallocated or popped off the stack

Converting Iterative to Recursive
 - In iterative functions information is utilized in a for or while loop to solve a problem while in a recursive function developed for the same purpose the information needs to be passed along recursively