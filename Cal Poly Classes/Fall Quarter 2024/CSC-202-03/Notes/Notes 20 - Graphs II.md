11/13/2024

[Slideshow Link](https://docs.google.com/presentation/d/1mvDdIguPS5aJs6OrhSQ5UEFzl9f7pjAMXTeLL1m3bv8/edit#slide=id.g26f241d31c1_0_156)

Traversal Options
 - Depth First Search, DFS
 - Breadth First Search, BFS

Depth First Search DFS
 - tie breaks alphabetically or numerically
 - explores an entire branch before returning to other branches
 - uses neighbors to navigate
 - because of ping-ponging due to cyclic nature, we create a visited set
 - on a directed set 

```
def dfs(graph: dict, node: int | None, visited: set = None) -> list[int]:
	if visited is None:
		visited = set()

	if node is None or node in visited:
		return []

	visited.add(node)
	result = [node]


	for neighbour in graph.get(node, []):
		result += dfs(graph, neighbour, visited)

	return result
```

Breath First Search
 - level by level exploration, adds all neighbors to list
 - also tie breaks alphabetically or numerically

```
def bfs(graph: dict, start: int | None) -> list[int]:
	if start is None:
		return []

	visited = set()
	result = []
	queue = [start]
	visited.add(start)

	while queue:
		current = queue.pop(0)
		result.append(current)

		for neighbour in graph.get(current, []):
			if neighbour not in visited:
				queue.append(neighbour)
				visited.add(neighbour)

	return result
```

Comparing 
 - BFS can potentially have a high space complexity due to holding all current level nodes
 - generally DFS is less intense
 - Both are $O(V + E)$ time complexity with V representing vertices and E representing edges
 - BFS ideal for shortest path, DFS suited for topological sorts, mazes
 - DFS has additional complexity with cycle detection due to backtracking
 - completeness - if there is a target, can you explore and find it with the shortest path
	 - BFS is complete
	 - DFS is not complete because it can get stuck in loops without careful implementation

Shortest Path
 - this is the primary goal in graph theory
 - obvious application
 - typically found using these traversal algorithms

Weights
 - edge weights
 - if multiple paths prioritize the cheaper one, decide what is more important, shortest path, or cost of path
 - Dijkstra's, Bellman-Ford, and A* all use these to find the best path possible

