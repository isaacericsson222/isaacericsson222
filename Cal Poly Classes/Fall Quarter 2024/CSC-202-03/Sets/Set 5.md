10/25/2024
[Set 5](https://canvas.calpoly.edu/courses/137532/assignments/1102906)

```
#Write a function to invert a binary search tree.

from __future__ import annotations
from dataclasses import dataclass

  
@dataclass(frozen = True)
class Node:
	value: int
	left: Node | None = None
	right: Node | None = None

  
  

def reverse_tree(root: Node | None) -> Node | None:
	if root == None:
		return None

	left_inverted = reverse_tree(root.left)
	right_inverted = reverse_tree(root.right)

	return Node(root.value, right_inverted, left_inverted)

root = Node(5, Node(3, Node(1), Node(4)), Node(7, Node(6)))

reverse_tree(root)
```


```
#Create a function that calculates the total of all the node values in a binary search tree.

from __future__ import annotations
from dataclasses import dataclass

@dataclass(frozen = True)
class Node:
	value: int
	left: Node | None = None
	right: Node | None = None

def sum_tree(tree: Node | None) -> int:
	if tree == None:
		return 0
		
	return tree.value + sum_tree(tree.right) + sum_tree(tree.left)

root = Node(5, Node(3, Node(1), Node(4)), Node(7, Node(6)))

sum_tree(root)
```
