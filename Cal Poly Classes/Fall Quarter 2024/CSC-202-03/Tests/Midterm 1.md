![[Midterm 1 (1).pdf]]

1.
	 A. time Complexity of Push for an ArrayStack
	 - best case is $O(1)$
	 - worst case is $O(1)$ 
	 B. time complexity of Insert for a linked list
	 - best case is $O(1)$
	 - worst case is $O(n)$
	 C. time complexity of Dequeue from linked list with direct access to tail
	 - best case is $O(1))$
	 - worst case is $O(n)$
	 D. time complexity of the function
	 - best case is $O(1)$
	 E. time complexity of the function
	 - worst case is $O(log(n))$
	 F. time complexity of the function
	 - worst case is $O(2^n)$

2.
	A. type alias for ListOfInts for list of ints
	`ListOfInts: list[int] = []`
	 B. type alas for StrOrFloat
	 `StrOrFloat: str | float`
	 C. type alias for Point
	 `Point: tuple[x: int, y: float]`
	 D. Node dataclass

```
@dataclass
Node:
Link: Node | None
```

	 E. function definition for linear_search

```
def linear_search(list1: list[int | str | float, target: int | string | float) -> bool:
```

3.
	 A. Insert at index i
	  - 
	 B.  Delete at index i
	  - 

4.
A.

```
#dataclass
class ArrayStack:
	capacity: int
	stack: list[tuple(str, int)]
	next: int
```

B.
```

@dataclass(frozen=True)
class Node:
	value: int
	next: Node | None = None
```

C. Queue = [3,4,6,5] ReadStack = 3 -> 4 WriteStack = 6 -> 5 DQ, DQ, NQ 2, DQ, DQ, NQ 1, NQ 6, DQ, DQ, NQ 7

Read stack = [1]

Write stack = [7]

5.
write a function that recursively traverses the linked list and returns only even ints in a new list

```
@dataclass(frozen=True)
class Node:
value: int
next: Node | None = None

def return_evens(list1: Node | None) -> Node | None:
	if not list1:
		return None

	if (list1.value % 2 == 0):
		return Node(list1.value, return_evens(list1.next))

	return return_evens(list1.next)
```

6.
write a function that recursively finds the minimum of a linked list

```
@dataclass(frozen=True)
class Node:
value: int 
next: Node | None = None

def find_min(list1: Node | None) -> int:
	if not list1:
		return min

	if list1.value < list1.next:
		min = list1.value
	else:
		return find_min(list1.next)

	return find_min(list1.next)
```