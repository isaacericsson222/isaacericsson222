10/21/2024

[Slideshow Link](https://docs.google.com/presentation/d/1ciY0qrEFw2FzoM85rCx4c8iHQuCZ03RFB9Kn5nRIh-o/edit#slide=id.g2ce5a569145_0_123)


Linear Search
 - Searches one by one
 - Time complexity is $O(n)$

```
def linear_search(arr: list[int], target: int, index: int = 0) -> int:
	if index > len(arr):
		return -1
		
	if arr[index] == target:
		return index

	return linear_search(arr, target, index + 1)
```

Binary Search
 - Init High set to array length, -1 if initially None
 - Base case returns None if low exceeds high
 - Midpoint calculates mid index using int division (low + high) // 2
 - Each time lowers amount it needs to search by half
 - Time complexity is $O(log(n))$

```
def binary_search(arr: list[int], target: int, low: int = 0, high: int = None) -> int | None:

	if high is None:
		high = len(arr) - 1
	if low > high:
	return None

	mid = (low + high) // 2
	guess = arr[mid]

	if guess == target:
		return mid

	elif guess > target:
		return binary_search(arr, target, low, mid - 1)
	else:
		return binary_search(arr, target, low, mid + 1)
```


**What we need to know for each sorting algorithm is how they work step by step**

Insertion Sort
 - Starts from second element and considers first element sorted
 - Compares current element to it's predecessors and then swaps if needed
 - Time complexity is $O(n^2)$ best case is $O(n)$

```
def insertion_sort(arr: list[int], i: int = 1) -> list[int]:
	if i >= len(arr)
		return arr

	key = arr[i]

	j = i -1

	new_arr = arr[:]

	while j >= 0 and new_arr[j] > key:
		new_arr[j + 1] = new_arr[j]
		j -= 1

	new_arr[j + 1] = key

	return insertion_sort(new_arr, i + 1)

```

Selection Sort
 - Similar swaps but we use the knowledge that the first must be the minimum to make it faster
 - Index 0 find the minimum
 - Also slow, time complexity is $O(n^2)$ best case is also $O(n^2)$ as well because it still checks minimum against all the rest in the list

```
def selection_sort(arr: list[int], start: int = 0) -> list[int]:
	if start >= len(arr) - 1:
		return arr

	min_idx = start
	for j in range(start + 1, len(arr)):
		if arr[j] < arr[min_idx]:
			min_inx = j

	new_arr = arr[:]

	#tuple swap, swaps at the index
	new_arr[start], new_arr[min_idx] = new_arr[min_idx], new_arr[start]

	return selection_sort(new_arr, start + 1)
```

Bubble Sort
 - Outer loops and inner loops
 - Similar to selection sort, but instead large numbers are bubbled up tot the end of the list
 - Does each bubble one by one even after it is sorted to check
 - Time complexity is also $O(n^2)$  best case it only runs once and is $O(n)$

```
def bubble_sort(arr: list[int],n: int = None ) -> list[int]:
	if n is None:
		n = len(arr)
	if n == 1:
		return arr

	new_arr = arr[:]

	for j in range(n - 1):
		if new_arr[j] > new_arr[j + 1]:
		new_arr[j], new_arr[j + 1] = new_arr[j + 1], new_arr[j]

	return bubble_sort(new_arr, n - 1)
```