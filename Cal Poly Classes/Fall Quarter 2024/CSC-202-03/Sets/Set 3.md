10/9/2024
[Set 3](https://canvas.calpoly.edu/courses/137532/assignments/1102904)

1.
Drawn

2.
```
from dataclasses import dataclass

@dataclass
class FixedSizeArray:
	size: int
	array: list
	next: int = 0

FixedSizeArray(10, [0, 0, 0, 0, 0, 0, 0, 0, 0, 0], 10)
```

3.
```

```

4.
The steps for accessing a middle element of a random ArrayList 
Because an array has access by index it takes just one step
1. Use the provided index to retrieve the data located there

5.
```
def insert(array_instance: FixedSizeArray, value: int, index: int) -> FixedSizeArray:

    if array_instance.next >= array_instance.size:

        #raise OverflowError("List is at full capacity")
		#this is what it would previously do

		while array_instance.next >= array_instance.size:
			resize(array_instance)

    if index < 0 or index > array_instance.next:

        raise IndexError("Index out of bounds")

  

    for i in range(array_instance.next, index, -1):

        array_instance.array[i] = array_instance.array[i - 1]

  

    array_instance.array[index] = value

    array_instance.next += 1

    return array_instance
```

6.
Linked Lists have dynamic memory storage meaning they do not need for clunky resizing functions

Linked Lists with their contiguous memory storage can avoid some severe situations where an arraylist does not have the room for additional data

Linked Lists have faster insertion and deletion operations in certain situations

7.
```

```

8.
Drawn

9.
ArrayLists has possibility of direct access for information that is $O(n)$

ArrayLists have minimal overhead as it only stores data and some padding

ArrayLists Insertion is quick in most cases, other than resizing

10.
Drawn