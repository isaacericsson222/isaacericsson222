11/20/2024

[Slideshow Link](https://docs.google.com/presentation/d/1xjUfp4NN1LdLBGMtj1oVjrX7Ko5xHbSRT77QkooHU9E/edit#slide=id.g2ce5e3b576a_0_117)

Topological Sort Applications
 - With a directed graph what order should you visit all the nodes?
 - use our class prerequisite as example
 - airlines
 - only works on DAGs or Directed Acyclic Graphs also depending on algorithm will not be unique
 - identify vertices with no incoming edge, those are starting points because no place leads to them, then 

Khans Algorithm
 - Compute in-degree of each vertex
 - create an empty queue to hold vertices with in-degrees of 0
 - add all with 0 to the queue
 - while the queue is not empty
	 - dequeue a vertex
	 - add to topological sort order
	 - for each vertex that has an edge from the recently dequeued vertex, reduce the vertexes in-degree by 1
	 - if any become 0 enqueue them. chooses the paths that will not have any other path to them

```
def kahn_topological_sort(graph: dict) -> list[int]:
	in_degree = {u: 0 for u in graph}
	for u in graph:
		for v in graph[u]:
			in_degree[v] += 1

	queue = [u for u in in_degree if in_degree[u]
	
	top_order = []
	while queue:
		u = queue.pop(0)
		top_order.append(u)
		for v in graph[u]:
			in_degree[v] -= 1
			if in_degree[v] == 0:
				queue.append(v)

	return top_order
```

DFS Topological Sort Algorithm
 - Traverse down a branch while a node has neighbors, only added once all have been explored
 - better with limited access to nodes
 - 

```
def dfs_topological_sort(graph: dict) -> list[int]:
	visited = set()
	stack = []

	def dfs(node):
		if node not in visited:
			for neighbor in graph.get(node, []):
				dfs(neighbor)

			visited.add(node)
			stack.append(node)

	for node in graph if node not in visited:
		dfs(node)

	return stack[::-1]
```