10/18/2024

[Slideshow Link](https://docs.google.com/presentation/d/1RJwKst0ybFMWCYLA_YuD3y5OUbl-t0Lxt5yFfXp7cUU/edit#slide=id.g26f242a629d_1_380)

Traversing
 - For linear data structures it is easy, for BSTs there are multiple options adding flexibility
 - Depth First Search and Breath First Search

Depth First Search
 - Going down a single branch as far as possible, and then accessing and printing the branches to the right
 - Utilizes a stack (through recursion or an explicit stack data structure) to keep track of the path ensuring every node is visited systematically.
 - Time complexity is $O(n)$ 
 - Pre-Order Traversal (prefix)
	- parent, left, right, when none is reached traces back one node and then attempts again

```
def preorder_dfs(node: Node | None) -> list[int]:
	if node is None:
		return[]
	return [node.value] + preorder_dfs(node.left) + preorder_dfs(node.right)
```
 - In-Order Traversal (infix)
	 - left, parent, right
	 - if you have a valid BST will sort your tree in numerical order

```
def inorder_dfs(node: Node | None) -> list[int]:
	if node is None:
		return[]
	return inorder_dfs(node.left) + [node.value] + preorder_dfs(node.right)
```

 - Post-Order Traversal (postfix)
	 - left, right, parent
	 - root will be last node visited

```
def postorder_dfs(node: Node | None) -> list[int]:
	if node is None:
		return[]
	return postorder_dfs(node.left) + postorder_dfs(node.right) + [node.value]
```

Breadth First Search
 - Visits root node, then all children, then all children, level by level
 - Uses a queue and visits node in a first in first out ordering meaning no generation is skipped

```
def bsf(root: Node | None) -> list[int]:
	if not root;
		return []
		
	result = []
	queue = enqueue(None, root)

	while queue:
		queue, current_node = dequeue(queue)
		result.append(current_node.value)

		if curreent_node.left:
			queue = enqueue(queue, current_node.left)
		if current_node.right:
			queeu = enqueue(queue, current_node.right)

	return result
	
```

BFS vs DFS
 - BFS is inherently suited for level-ordered traversal which can be useful for visualization of nodes level by level
 - BFS Shortest path concept is more nuanced in BFSs because it is easy to count edges this way which is useful for minimum-depth problems
 - BFS is naturally suited for wider trees but not deeper ones
 - BFS can also be used to verify if a BST is balanced by checking the depth of the shallowest and deepest leaf nodes without having to traverse every single path