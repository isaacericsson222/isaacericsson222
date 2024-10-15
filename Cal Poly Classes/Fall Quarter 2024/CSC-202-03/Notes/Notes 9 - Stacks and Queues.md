10/14/2024

[Slideshow Link](https://docs.google.com/presentation/d/184C0sKjkGxgpZOvTRkcs8dDjL0RHV8I-nH6HcZ9iCFU/edit#slide=id.g2cd95aac0ed_0_338)

Array Queues Downsides
 - Highly mutable and side effect heavy
 - To avoid these side effects we can use stack node

Stack Node - linked list representation of a Queue
 - Combination of data structures
 - Can push to top of the stack

```
from __future__ import annotations
from dataclasses import dataclass

@dataclass(frozen=True)
class Node:
	value: int
	next: Node | None = None

stack = Node(4, Node(3, Node(2, None)))
```

To append a new head
 - $O(1)$ operation

```
stack = Node(4, Node(3, Node(2, None)))
stack = Node(5, stack)
```

Removing a new head
 - Also $O(1)$ operation
 - Check to see if empty

```
stack = stack.next
```

Peek
 - Also $O(1)$
 - returns head

Linked List Queue Implementation
 - Head operations (first in line operations are fast), but tail operations, adding to queue, are slow
 - No tail pointer to prevent mutations

Enqueue
 - Traverse until none tail to enqueue at end
 - $O(n)$ operation

```
def enqueue(current: Node | None, value: int) -> Node:
	if current is None:
		return Node(value)

	return Node(current.value, enqueue(current.next, value))
```

Dequeue
 - Direct access to head we just need to remove it 
 - $O(1)$ operation

```
def dequeue(head: Node | None) -> Node | None:
	if head is None:
		raise IndexError("queue underflow.")

	return head.next, head.value
```

Peek
 - Direct access just returns head
 - $O(1)$ operation

```
def dequeue(head: Node | None) -> Node | None:
	if head is None:
		raise IndexError("queue underflow.")

	return head.value
```

Optimization
 - Based on the needs of the code you can flip the access operations to favor the tail or the head of the linked list
 - Equivalent in structures but swaps time complexities (enqueue is now $O(1)$)
 - changes next to prev
 - Why use this? 
 - Read-Heavy applications are ones with frequent dequeue operations should be head only
 - Write-Heavy applications where enqueue is most common should be tail only

Amortized Anlysis
 - A mortgage where you put a down payment and the rest is amortized cut up into monthly payments
 - Payments over time
 - If you use the $O(n)$ operation just once to provide information for many $O(1)$ operations you have divided the cost amongst cheap operations
 - Create a reversed stack or queue where you can then use a $O(1)$ operation at all times

Two Stack
 - A read stack (read with $O(1)$ push and pop operations, and a write stack (write with $O(1)$ operations)
 - We add to the write stack and remove from the read stack
 - When the read stack is empty we reverse the write stack onto the read stack
 - Time complexity is $O(1)$ because $$\frac{O(n)}{n} = 1$$

 