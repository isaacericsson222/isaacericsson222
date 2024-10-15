10/02/2024

[Slideshow Link](https://docs.google.com/presentation/d/1qghiO5CMHn2S8iwTrMaiajn-Psle_Qu50LyO75TyREE/edit?usp=sharing)

Freedom Concerns
 - Allows accessing all data at once
 - Modification is allowed
 - Unsafe operations
 - We *Want* less freedom

Limited Data Structure
 - Stack allows only for adding or removing from the top of the stack, called push and pop
 - "Last in, First Out" LIFO last place you put is first one off

Call Stack
 - Used to manage order of execution for functions

Stack ADT(Abstract Data Type)
 - Operates on LIFO principle
 - Operations Push(x), Pop(), Peek(), IsEmpty()
 - Limited operations as a strength, protecting data, ensures efficiency when it is aplicable, such as undo mechanisms

Stack Implementations - Concrete
 - Array-Based Implementation
 - Combines the benefits of an array with stack benefits, Memory Access, Size Limitations, Implementation
 - When List-Based, it has dynamic size, but memory overhead.

ArrayList Implementation
```
from dataclasses import dataclass
#dataclass
class ArrayStack:
	capacity: int
	stack: list
	next: int
```

 - LIFO manner, next usually points to the top, if over pushed leads to a stack overflow

Operations - Push
 - Check for space
 - Add to top

```
def push(stack: ArrayStack, value: int) -> ArrayStack:
	if stack.next == stack.capacity:
		raise IndexError("Stack Overflow")

	stack.stack[stack.next] = value
	stack.next += 1

	return stack
```

Operations - Pop
 - Grabs whatever is at the top and remove it
 - Operates similar to push
 - if called on an empty stack results in stack underflow
 
```
def pop(stack: ArrayStack) -> tuple[ArrayStack, int]:
	if stack.next ==0:
		raise IndexError("Stack Underflow")

	value = stack.stack[stack.next-1]

	stack.stack[stack.next - 1] = None
	stack.next -= 1

	return stack, value
```

Operations - Peek
 - Returns value of whatever is at the top of the stack

```
def peek(stack: ArrayStack) -> int:
	if stack.next == 0:
		raise IndexError("Stack Underflow")

	return stack.stack[stack.next - 1]
```

Application of Stack - Recursion
 - For example the call stack for a Fibonacci sequence all get added to the stack, then returned by removing from the stack in a timely order

Polish Notation
 - Prefix notation and Postfix notation
 - Prefix + 3 4
 - Postfix 3 5 +
 - Used in stacks to make things easier
 - Traverse left to right, operands add to out, pushed onto stack, follow order of operations however, so add to stack if top is empty or has less priority
 - else: pop everything until less than
 - 3 + 4 * 6 / 7 - 5 --> 3 4 6 * 7 / + 5 -

Operations - Resize
 - Goal is to create a larger stack with increased capacity while maintaining correct order of elements
 - New capacity is current capacity * factor
 - Temporarily stack to reverse the order of elements, will be reversed again into larger stack

Time Complexities
 - Usually $O(1)$ Pop and Push and Peek
 - Resize best case is $O(1)$ but worst case and time complexity is $O(n)$
 - All are relatively fast