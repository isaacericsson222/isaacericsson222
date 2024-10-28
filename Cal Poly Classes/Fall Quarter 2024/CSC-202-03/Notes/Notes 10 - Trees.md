10/16/2024

[Slideshow Link](https://docs.google.com/presentation/d/1o7xEJyV-w_fxItHnxVffp8gPoUGX_WAESpqcXvWSHig/edit#slide=id.g26f2471d749_2_420)

Applications of Trees
 - family trees
 - file Structures
 - skill trees

Tree Abstract Data Type - N ary Tree
 - a Node that can have n number of childs or other nodes
 - binary search trees have zero, one, or two children (bi - two)
	 - left child of a Nodes value must be less than the parent
	 - right child of a Nodes value must be greater than the parent

Trees
 - Root Node: head of the tree
 - Sub-tree: child node that can root another tree
 - Levels: distance of nodes from root
 - Degree: how many nodes a tree has
 - Leaf Nodes: Nodes without children
 - Height of the Tree: maximum level of any node in tree
 - Edges: lines connecting the tree
 - Relationship: child under parent
 - siblings: share the same parent
 - Depth: number of edges from a node to the root
 - Balance: height differences between subtrees

```
from __future__ import annotations
from dataclasses import dataclass

@dataclass(frozen = True)
class Node:
	value: int
	left: Node | None = None
	right: Node | None = None
```

**Operations**

Searching
 - uses the BST(binary search tree) properties compares the value and follows the tree
 - if leaf node is found without encountering the desired value return -1
 - time complexity of find is $O(log(n))$ because you divide your search base in half each time

```
def find(node: Node| None, value: int) -> bool:
	if node is None:
		return False
		
	elif value == node.value:
		return True
		
	elif value < node.value:
		return find(node.left, value)
		
	else:
		return find(node.right, value)
```

Insertion
 - again use the BST properties to find where the new Node should be placed
 - append an new value at a leaf
 - same time complexity as search $O(log(n))$
 - duplicates are decided upon implementation, put to the right in this code but you can choose
 - no consideration for balance, can create a unbalanced tree that effects performance

```
def insert(node: Node | None, value: int) -> Node:
	if node is None:
		return Node(value)

	elif value < node.value:
		return Node(node.value, insert(node.left, value), node.right)

	else:
		return Node(node.value, node.left, insert(node.right, value))
```

Minimum
 - finding min is easy just traverse to leftmost node
 - max is the same
 - time complexity depends on the balance of the tree $O(n)$ or $O(log(n))$ or best case $O(1)$

```
def min_value_node(node: Node) -> Node:
	if node.left is None:
		return node
	else:
		return min_value_node(node.left)
```

Deletion
 - might remove a node and requires to maintain BST, more complex
 - search for node then remove and correct
 - different implementations, some can lead to more balanced trees
 - Time complexity is $O(log(n))$ usually but unbalanced is $O(n)$ 

```
def delete(node: Node | None, value: int) -> Node:
	if node is None:
		return None

	if value < node.value:
		return Node(node.value, delete(node.left, value),node.right)

	elif value > node.value:
		return Node(node.value, node.left, delete(node.right, value))

	else:
		if node.left is None:
		return node.right

		if node.right is None:
			return node.left

		successor = min_value_node(node.right)

		return Node(successor.value, node.left, delete(node.right, successor.value))
```