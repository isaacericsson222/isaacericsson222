11/22/2024

[Slideshow Link](https://docs.google.com/presentation/d/1a0y_drnxyKoWrboRxFUIzFsMtB7rlbIWupiGkv8dpCI/edit#slide=id.g26f2495d72b_0_266)

BSTs
 - good but have no way to orient itself to orient $O(log(n))$ performance
 - heaps are balanced but no search :(

Self Balancing Trees
 - difficult to code

Red Black Tree(RBT)
 - each node contains a extra bit to store the color, either red or black
 - the root of the tree and all NIL(leaf) nodes are Black
 - Nodes are Red or Black, if a node is Red, both it's children must be black
 - all paths from a node to it's NIL  must contain the same number of Black Nodes, ensures roughly equal search depths

```
#same as BST but with color
@dataclass
class Node:
	value: int
	color: str
	left: Node | None = None
	right: Node | None = None
```

Insertion
 - guarantee that you do not violate the RBT properties as well as the BST properties and you will get a valid and balanced BST
 - nodes are always inserted as red and placed in the appropriate location following the BST properties
 - this leads to a temporary violation of having two reds in a row solved through rotation
 - or recoloring, this is changing the colors of the parent, uncle or grandparent of the nodes
 - this is a lightweight fix

AVL Trees
 - self balancing trees
 - also use a pointer but instead keep track of how unbalanced it is compared to its neighboring branches
 - uses this to then rotate to change the tree around