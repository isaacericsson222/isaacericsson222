[Slideshow Link](https://docs.google.com/presentation/d/1vdNclEJ-XjMVlGo4YkkllN8ihI5TygIe7Sqz65LfjpI/edit?usp=sharing)

Downside of ArrayLists
 - Memory allocation is poor
 - Resizing mechanism is needed to often and doubles some capacity

Linked Lists
 - Structure where each successive element is accessed via a reference from its predecessor
 - Access method is not an index pointed but instead accessed sequentially
 - More efficient memory because there is almost always storage

Node Composition
 - Each node holds a data value and a reference to subsequent node
 - Always start at the head and traverse from it
 - Termination ends with a None value indicating no further nodes, the tail


```
from __future__ import annotations
from dataclasses import dataclass


@dataclass (frozen = True)
class Node:
	value: int
	nextL Node | None = None


linked_list = Node(4, Node(3, Node(2, None)))
print(linked_list)

#Node(value = 4, next=Node(value=3,next=Node(value=2,nexNone)))
```

 - Frozen = True means immutable
 - value: int defines the datatype

Linked List Operations
 - How to access by Index
	 - Iterative process starting at the head using a counter (index)
	 - Recursive implementation of the function base case is none(out of bounds)
	 - Time complexity is $O(n)$
 - Search
	 - Search works similar to access by Index
	 - Returns None if not found

Immutable Linked List
 - How to modify
	 - Create a new linked list as you traverse the old one
	 - Uses a recursive function to grab the next node and then return a completed copied list
 - Append
	 - To add to the head is simple because we have access to the head node(val 3, next = l) 
		 - (l is the list that is being added to the end of 3)

```
def add_new_head(current_head: Node| None, value: int) -> Node:
	return Node(value, current_head)
```

 - Append to end
	 - To add to the tail iterate through the list recursively creating a new Node each time until none is reached, then return Node(4, None) or Node(4) (4 is appended)
	 - Time complexity of both of these is $O(n)$

```
def append(current: Node | None, value: int) -> Node:
	if current is None:
		return Node(value)

	return Node(current.value, append(current.next, value))
```

- Insert
	- Locate position based on index
	- Move sequentially keeping a counter and copying as you traverse
	- Once position is found insert and link to next
	- Time complexity is $O(n)$

```
def insert_at_position(head: Node | None, value: int, position: int) -> Node:
	if position < 0
		raise IndexError("Position must be a non-negative integer")

	if head is None or position == 0
		return Node(value, head)

	new_next = insert_at_position(head.next, value, position - 1)
	return Node(head.value, new_next)
```

 - Delete
	 - Similar to insert, traverse to position set next pointer of previous node to next node instead effectively bypassing the node and excluding it from the list
	 - Special cases include deleting the head where you must update the head to be next node
	 - This does not delete from memory, time complexity is also $O(n)$

```
def delete_at_position(head: Node | None, position: int) -> Node:
	if position < 0:
		raise IndexError("Position must be a non-negative integer")

	if head is None:
		raise IndexError("Position out of bounds")

	if position == 0:
		return head.next

	new_head Node(head.value, delete_at_position(head.next, position -1))
	return new_head
```

 - Size
	 - Start at the head and traverse while keeping a count
	 - Time complexity is $O(n)$ because of traversal

```
def calculate_length(current: Node| None) -> int:
	if current is None:
		return 0

	return 1 + calculate_length(current.next)
```


ArrayList vs LinkedList
 - Memory allocation is better in a Linked list due to easier resizing and not chunked storage
 - Time complexity is longer in Linked list, ArrayLists have direct access $O(1)$
 - LinkedList has a higher overhead (extra resources needed to complete a task) than ArrayList