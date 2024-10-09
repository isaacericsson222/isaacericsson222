10/4/2024

[Slideshow Link](https://docs.google.com/presentation/d/1nhhtyWtDiHLBdQI-iC-Gx19qZ41uGoTboUI0XYF-QJQ/edit#slide=id.g2cbb1b8ee8c_0_5)

List Abstract Data Type
 - A collection of items where each hold a position within the list
 - Key Operations:
	 - Insert
	 - Delete
	 - Find
	 - Access
 - Important property is ordering which can be indexed

Arrays
 - List is a (dynamic array)
 - Homogeneous all elements must be the same, hard to implement
 - Have a fixed size, once created it can't be changed
 - Ordered collection

Array Class Attributes
 - size - the size of the array
 - array - list represents the actual data storage
 - next - int = 0 tracks next available position

Accessing by Index
 - Access directly by index Arr[5] goes right to element at 5
 - Highly efficient
 - Important to index bound the function done through position checks
 - Also important to raise a ValueError if none at index
 - Time complexity is $O(1)$ because each memory index has a key

Append
 - Puts data in next available position, starting at lowest free index
 - Use if array_instance.next >= array_instance.size: to raise an OverflowError telling that the list is at full capacity
 - After appending remember to increment next in order to set it to the next available position
 - Also $O(1)$

Search
 - At each index grab and compare to target, a loop
 - No prior sorting is required, brute force search
 - Can be a recursive function
 - Return -1 if not found, purely convention
 - Time complexity $O(n)$ it loops through the loop can be $O(1)$ if first item in the list

Insert
 - To add a specific index within the array
 - Check if valid (in arrays capacity) (Otherwise Overflow Error)
 - Check capacity for other elements that it shifts (Otherwise IndexError)
 - Now shift the elements using a loop
 - Then insert the value
 - Time complexity is $O(n)$ and best case is $O(1)$

Delete
 - Shift all elements back by one removing the element at index in the process
 - Check if valid index (Otherwise IndexError)
 - Also a for loop to shift
 - Time complexity is $O(n)$ and best case is $O(1)$

Considerations of a List as an Array
 - Fixed size is important note, makes it memory efficient, but resizing can be resource-intensive
 - An ArrayList is an implementation of an array as a list
 - has array features of a list and an array

Resizing
 - When an array list is filled to capacity, checks that would return an Overflow Error instead call a function to resize)
 - Resizing creates a brand new array that has say twice the space for twice the amount of elements
 - It is expensive to resize
 - Time complexity is $O(n)$ 

Python List
 - Dynamic arrays, automatically resizes
 - Python over allocates memory for this
 - Type Flexible
 - Motivation for linked list is due to memory limitations cause by resizing etc