10/25/2024

[Slideshow Link](https://docs.google.com/presentation/d/1R2NH7_q0TxhX9_Ux1_-y9udg9-xITGWyBerlKHYq23w/edit#slide=id.g26f23817af3_0_165)

Limitations of BSTs
 - Are efficient but drawbacks include unbalanced trees
 - finding 2nd min is difficult and other mins etc 

Heap ADT
 - a heap is a specialized tree that satisfies the heap property
 - the parent must be greater than it's children
 - ours will be binary heaps, so very tree like just without the BST property
 - max heaps has max at the top, min heap has min at the top
 - heapify operation adjust tree to suite the heap property
 - in actuality the heap is represented as a tree but is in reality an array

Parent-Child Relationship
 - for any element at index i
 - the left child is at 2i + 1
 - the right child is at 2i + 2
 - conversely, the parent of any element(other than the root) is at index (i-1)/2

```
from dataclasses import dataclass

@dataclass(frozen=True)

class MaxHeap:
	data: list[int] = field(default_factory=list) #ensures it is an empty list
```

Heapify
 - called whenever something modifies the heap
 - used after insertion, deletion, and creation
 - checks if a node violates heap property, then swaps if a violation occurs
 - after a swap recursively applies heapify starting from the swapped node
 - depends on if min or max heap

Insertion
 - adds an element to the end of the list, and then ensures that is adheres to heap property
 - time complexity is $O(log(n))$ but does have a best case of $O(1)$

```
def insert(heap: MaxHeap, element: int):
	new_heap_data = heap.data[:] + [element]

	last_index = len(new_heap_data) - 1

	new_heap = heapify_up(MaxHeap(new_heap_data), last_index)

	return new_heap
```

Heapify_up
 - time complexity on balanced tree is $O(log(n))$ 
 - compares elements to their parent and then swaps, if swap occurs recalls heapify up passing back the parent

```
def heapify_up((heap: MaxHeap, index: int)) -> MaxHeap:
	if index == 0:
		return heap

	parent_index = (index - 1) // 2
	heap_data = heap.data

	if heap_data[index] > heap_data[parent_index]:
		new_heap_data = heap_data[:]

		new_heap_data[index], new_heap_data[parent_index] = new_heap_data[parent_index], new_heap_data[index]
	return heapify_up(MaxHeap(new_heap_data), parent_index)

	else:
		return heap
```

Peek
 - retrieves top element
 - no modifications
 - $O(1)$

```
def peek(heap: MaxHeap) -> int:
	if heap.data:
		return heap.data[0]
		
	raise IndexError("peeked on empty heap!")
```

Extraction
 - removes and returns top element of the heap
 - first remove, then reorganize heap
 - time complexity is $O(log(n))$ best case is $O(1)$

```
def extract_max(heap: MaxHeap) -> tuple[MaxHeap, int]:
	if not heap.data:
		raise ValueError("Heap is empty")

	max_element = heap.data[0]

	new_heap_data = heap.data[:]

	last_index  len(new_heap_data) - 1

	new_heap_data[0] = new_heap_data[last_index]
	new_heap_data = new_heap_data[:last_index]

	new_heap = heapify_down(MaxHeap(new_heap_data), parent_index)

	else:
		return heap
```

Heapify_down

```
def heapify_down(heap:MaxHeap, index:int) -> Maxheap:
	heap_data = heap.data
	current_size = len(heap_data)
	largest = index
	left = 2 * index + 1
	right = 2 * index + 2

	if left < current_size and heap_data[left] > heap_data[largest]:
		largest = left

	if right < current_size and heap_data[right] > heap_data[largest]:
		largest = right

	if largest != index:
		new_heap_data heap_data[:]
		new_heap_data[index], new_heap_data[largest] = new_heap_data[largest], new_heap_data[index]

	return heapify_down(MaxHeap(new_heap_data), largest)

	return new_heap, max_element
```

Heapify a Random List
 - create a new heap
 - make sure you know if your heap should be max or min because the operators for the check sin max or min change directions
 - starts with first non leaf node
 - time complexity is $O(n \ log(n))$ best case is $O(n)$ already sorted and just checking

```
def build_heap(elements:list[int]) -> MaxHeap:
	heap = MaxHeap(elements[:])

	n = len(heap.data)

	for i in range(n //2 -1, -1, -1):
		heap = heapify_down(heap, i)

	return heap
```

Heap Sort
 - take a list and convert it to a heap and then repeatedly remove the root of the heap (the largest of smallest element)
 - if you want from high to low use max heap, if you want low to high use a min heap
 - results in a time complexity of $O(n \ log(n))$ 
 - works as a sort, but uses a more memory than other sorts