10/23/2024

[Slideshow Link](https://docs.google.com/presentation/d/1ZhLM0rENht0-dIfAJGvQJ_1Keqyn_ywDAmGeEuI0Ow8/edit#slide=id.g26f2423cea6_0_175)

Sorting $O(n^2)$
 - insertion, selection, and bubble sort are all slow with time complexity

Divide and Conquer Algorithms
 - break up the problem into simple small segments then solve
 - Seen in binary search

Stable (definition)
 - A sorting algorithm is stable if it preserves the relative order of equal elements in the sorted output
 - For example if two numbers that are equal the first instance of the number will still go first in a stable algorithm
 - examples are Insertion and Bubble Sort because same numbers are not swaped while selection sort swaps everything anyways

Merging to Lists
 - creates an empty list
 - base cases are if all elements in left or right are merged append the remaining elements from the opposite side
 - appends smaller elements to merged list
 - divides and conquers, splits lists until each list is one, then re combines while sorting
 - is stable in the case of multiples of a number(takes the left one)
 - time complexity is $O(n)$

```
def merge(left: list[int], right: lsit[int], merged: list[int] = None, left_index: int = 0, right_index: int = 0) -> list[int]:
	if merged is None:
		merged []

	if left_index >= len(left):
		return merged + right[right_index:]
	if right_index >= len(right):
		return merged + left[left_index:]

	if left[left_index] < right[right_index]:
		return merge(left, right, merged + [left[left_index]], left_index + 1, right_index)
		
	else:
		return merge(left, right, merged + [right[right_index]], left_index, right_index + 1)
```

Merge Sort
 - breaks up list and then calls merge
 - overall is time complexity of $O(n \ log(n))$ because of the combination of divide $O(log(n))$ and conquer $O(n)$ 
 - $O(n \ log(n))$ is slower than $O(n)$ but faster than $O(n^2)$ 

```
def merge_sort(arr: list[int]) -> list[int]:
	if len(arr) <= 1:
		return arr

	mid = len(arr) // 2
	left_sorted = merge_sort(arr[:mid])
	right_sorted = merge_sort(arr[mid:])

	return merge(left_sorted, right_sorted)
```

Quick Sort
 - another divide and conquer sorting algorithm, but chooses a pivot element
 - elements less than pivot go left and greater elements go right
 - continues until we can't partition anymore
 - time complexity has a lot of variants, best case is $O(n \ log(n))$, average case is also $O(n \ log(n))$, and worst case is $O(n^2)$
	 - worst case is because if the worst decision is made each time the $log(n)$ does not occur and instead splitting the list repeatedly happens $n$ times
 - Quick sort is optimal for sorting large datasets because the average time complexity really shows ups in large databases
 - 




```
def quicksort(arr: list[int]) -> list[int]:
	if len(arr) <= 1:
		return arr

	less, equal, greater = partition(arr, - 1)

	return quicksort(less) + equal + quicksort(greater)
```

Partition
 - algorithm that selects pivot and classifies elements as less than or greater than pivot element
 - technically any element can be chosen for pivoting
	 - Lomuto (simple): pivot is last element
	 - Hoare (Original): can be any element more efficient than Lomuto
	 - Middle Pivot: chooses middle element, potentially better
	 - Randomized Pivot: avoids worst-case maintains $O(n \ log(n))$ time complexity

```
def partition(arr: list[int], index: int) -> tuple[list[int]], list[int], list[int]]:

	pivot = arr[index]
	
	#x for x in arr if x < pivot is the same as
	#for x in arr
		#if x < pivot:
			#less.apppend(x)

	less = [x for x in arr if x < pivot]
	equal = [x for x in arr if x == pivot]
	greater = [x for x in in arr if x > pivot]

	return less, equal, greater
```

Tim Sort
 - pythons sorting algorithm, great for performance and adaptability, actual source code is written in C
 - should use this almost all the time unless really specific looking for something

```
def timsort(array):
	min_run = identify_min_run(size(array))
	for each segment in array:
		insertion_sort(segment[0:min_run])
	size = min_run
	while size < len(array):
		for start in range(0, len(array), 2 * size):
			mid = start + size - 1
			end = min((start 2 * size - 1), (len(array) - 1))
			merged_array = merge(array[start:mid], array[mid + 1: end])
			array[start : end + 1] = merged_array 
			size *= 2
```