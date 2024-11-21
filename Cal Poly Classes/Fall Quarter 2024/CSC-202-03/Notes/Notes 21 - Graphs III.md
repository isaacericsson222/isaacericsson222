11/15/2024

[Slideshow Link](https://docs.google.com/presentation/d/1pLHW7kmfQAeqokdsvMeMyhu1fwO6x61WJJU9FK_rOPs/edit#slide=id.g26f2469f589_0_88)

Dijkstra's Algorithm
 - shortest path algorithm
 - can handle directed and undirected graphs
 - can handle weighted and non weighty graphs, not negative weights though
 - application is driving networks
 - like dfs, but keeps track of edges as well
 - manage a visited set, a priority queue, and parent set
 - an exhaustive search that finds the shortest distance from any node

```
def dijkstra(graph: HashMap, start: str) -> tuple[dict[str, float], dict[str, str]]:
	distances = {n: float('infinity') for n, _ in graph.data if n != ' '}
	distances[start] = 0
	parents = {n: None for n, _ in graph.data if n !- ' '}

	parents[start] = start
	pq = MinHeap()
	pq = enqueue(pq, (start, 0))

def dijkstra(graph: dict, start: int):
	while pq.data:
		print(pq)
		pq, (current_vertex, current_distance) = dequeue(pq)
		neighbors = get_neighbors(graph, current_Vertex)

		for neighbor, weight in neighbors:
			distances = current_distance + weight
			if distances < distances[neighbor]:
				distances[neighbor] = distances
				parents[neighbor] = current_vertex
				pq = enqueue(pq, (neighbor, distance))

	return distances, parents
```

A* Algorithm Example
 - A* uses a heuristic, some nodes are estimated to be close to the final solution
 - A* is better when you have a good heuristic function, and the goal location is known
 - Dijkstra's can be useful for a guaranteed shortest path with exploration of other locations