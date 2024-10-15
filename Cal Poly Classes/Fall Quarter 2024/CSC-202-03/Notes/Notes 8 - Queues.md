10/09/2024

[Slideshow Link](https://docs.google.com/presentation/d/1qaGQzkgJXRb8EDa47oydn3Id5YU2jeXiYmtqZmbC2mA/edit#slide=id.g2cd3f257759_0_184)

Stacks Review
 - LIFO (last in first out), push and popping only off the top
 - Simple to use, memory safety
 - Cons are limited access, maybe not the best structure

Introducing Queues
 - FIFO (first in first out), basically a line
 - Operations are enqueue, add element to back of queue, and dequeue, remove element from front of the line. Peek views the front of the line, isEmpty checks if the queue is empty
 - Either array or linked list implementation

Applications
 - Real life line management
 - Printer spooling also works in a queue 
 - Spotify queue
 - Streaming services
	 -  taking incoming data chunks and placing them in a buffer queue

Implementation
 - Array, linked list, two stacks, circular buffer
 - Today will be array based brings in the pros and cons of an array

```
from dataclasses import dataclass

@dataclass
class ArrayQueue:
	capacity: int
	Queue:: list
	tail: int
```

Enqueue
 - Space is limited, need to check if space (tail index > or < capacity>?) == (Queue overflow)
 - Directly modify index that was being stored with tail and then increment tail to next index
 - Looks a lot like push

```
def enqueue(queue: ArrayQueue, value: int) -> ArrayQueue:
	if queue.tail >= queue.capacity:
		print("Queue overflow! Cannot enqueue.")
		return queue

	queue.Queue[queue.tail] = value
	queue.tail += 1

	return queue
```

Dequeue
 - Check for Queue Underflow, index 0 is always the head, what if it's empty?
 - Removing an element from the front requires shifting down all other elements
 - Last spot set to none and tail pointer is also updated -1
 - Because it is returned as a tuple, special syntax is needed. Val, Q = dequeue(Queue) (tuple unpacking)

```
def dequeue(queue: ArrayQueue) -> tuple[Any, ArrayQueue]:
	if queue.tail == 0:
		print("Queue Underflow! Cannot dequeue.")
		return None, queue

	dequeued_value = queue.Queue[0]

	for in range(1, queue.tail):
		queue.Queue[i - 1] = queue.Queu[i]

	queue.Queue[queue.tail - 1] = None
	queue.tail -= 1

	return dequeued_value, queue
```

Peek
 - All we do is look at Queue[0], check to see something is there to peek at

```
def peek(queue: ArrayQueue) -> int:
	if queue.tail == 0:
		print("Queue is empty! Nothing to peek.")
		return None

	return queue.Queue[0]
```

Time Complexity
 - All are $O(1)$ except for the average and worst case of Dequeue which are $O(n)$ This is because of the for loop involved in shifting each element

Problem
 - Oven is a queue of pizza orders in tuples that need to be passed into the oven and have their cook number decreased by one

Array Queue
 - Direct index memory is nice however it is fixed size
 - Trick to improve memory usage is the circular queue

Circular Queue
 - Removes the shifting function and instead changes front pointer to point at next index
 - This utilizes Modulus for indexing (% operator)
 - enqueue would be (tail + 1) % capacity
 - dequeue would be (front + 1) % capacity
 - Tail wraps around to the front
 - Changes time complexity of the Queue function to be all $O(1)$

```
from dataclasses import dataclass

@dataclass
class CirucularQueue:
	capacity: int
	queue: list
	front:int = 0
	tail: int = -1
```

Resize
 - Expand when full by doubling size
 - Not like array, utilizes dequeue and enqueue
 - Time complexity of this is $O(n^2)$ because it is a while loop containing dequeue(utilizes a for loop) best case is $O(1)$ if single operation

```
def resize(queue: ArrayQueue) -> ArrayQueue:
	new_capacity = queue.capacity * 2
	new_queue = ArrayQueue(new_capacity, [None] * new_capacity)

	while queue.tail > 0:
		value, queue = dequeue(queue) #tuple unpacking
		new_queue = enqueue(new_queue, value)

	return new_queue
```

