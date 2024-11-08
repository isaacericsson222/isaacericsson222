11/05/2024

[Set 6](https://canvas.calpoly.edu/courses/137532/assignments/1102907)

1. Insertion sort time complexity on an already sorted list each is compared to the past so it is $O(n)$ 
2. Bubble sort on a list that is completely in the incorrect order each element makes n comparisons so $O(n^2)$ 
3. using binary trees inorder traversal, n inserts to the tree which is $O(log(n))$ then the time complexity of inorder traversal is an $O(n)$ operation so best case would be a tree of length 1 that requires an $O(n \ log(n))$ operation, worst case would be $O(n^2)$
4. Selection Sort, Merge Sort, Insertion Sort
 - Selection Sort is best case $O(n^2)$ 
 - Merge Sort is best case $O(n \ log(n))$ 
 - Insertion Sort is best case $O(n)$ 
 5. 5. Here is a starting list [3,4,2,1,6,7,3,8,9,10]. Draw what the left and right partitions are when the pivot is:

 -  1
  [] [1] [1]  [3,4,2,6,7,3,8,9,10]

 - 10
 [3,4,2,1,6,73,8,9]  [10]  []

 -  6
 [3,4,2,1,3]  [6]  [7,8,9,10]

 -  3
 [2,1]  [3, 3]  [4,6,7,8,9,10]

6. [2,1,3,2,4,5,7]
 - [1,2,3,2,4,5,7]
 - [1,2,2,3,4,5,7]
 - [1,2,2,3,4,5,7]

7.
```
def selection_sort(arr: list[tuple], start: int = 0) -> list[tuple]:
	if start >= len(arr) -1:
		return arr

	min_idx = start
	for j in range(start + 1, len(arr)):
		if arr[j][1] < arr[min_idx][1]:
			min_idx = j
	new_arr = arr[:]
	new_arr[start], new_arr[min_idx] = new_arr[min_idx], new_arr[start]
	return selection_sort(new_arr, start + 1)

  

listOfTuples = [("hi", 50), ("john", 20), ("jason", 23)]

  

print(selection_sort(listOfTuples))
```

8. [3,2,1,5,6,7,3]
 is it smallest to largest or largest to smallest
 [3,2,1,5,6,7,3] max_idx is [0] 3
 [3,2,1,5,6,7,3] max_idx is [0] 3
 [3,2,1,5,6,7,3] max_idx is [3] 5
 [5,2,1,3,6,7,3] max_idx is [4] 6
 [6,2,1,3,5,7,3] max_idx is [5] 7
 [7,2,1,3,5,6,3] max_idx is good now repeat with start + 1
 [7,3,1,2,5,6,3]
 [7,5,1,2,3,6,3]
 [7,6,1,2,3,5,3] max_idx is good now repeat with start + 1
 [7,6,2,1,3,5,3]
 [7,6,3,1,2,5,3]
 [7,6,5,1,2,3,3] max_idx is good now repeat with start + 1
 [7,6,5,2,1,3,3]
 [7,6,5,3,1,2,3] max_idx is good now repeat with start + 1
 [7,6,5,3,2,1,3]
 [7,6,5,3,3,1,2] max_idx is good now repeat with start + 1
 [7,6,5,3,3,2,1] max_idx is good now repeat with start + 1

9. Visually represent the concept behind the O(n log n) time complexity of Merge Sort.
 The list is split in half until each list is only one element long representing the $O(log(n))$ time complexity, then each comparison is made representing a $O(n)$ time complexity, note this is not $O(n^2)$ time complexity for the secondary part like other sorting algorithms as it does not need to make as many comparisons each step

10. Use a table to keep track of binary search of x = 6 on this list = [1,2,5,6,7,8,9,10,11,12,14,16,17,19]
 
 
 
