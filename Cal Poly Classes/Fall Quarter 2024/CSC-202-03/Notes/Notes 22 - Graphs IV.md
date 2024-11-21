11/18/2024

[Slideshow Link](https://docs.google.com/presentation/d/13hSCLydGJxv671NBcAh7R6lVaB8RbVK2aUuhJItuRiA/edit#slide=id.g2720ec22e85_0_0)

Introduction to Minimum Spanning Trees (MST)
 - How do we minimize visiting every node in a graph
 - connects all vertices without cycles
 - spanning Tree: A subgraph that includes all the vertices of the original graph with a minimum number of edges required to maintain connectivity, forming a tree.

Prim's Algorithm Overview
 - Initialize any vertex as starting point, use priority queue to track edges and weights
 - greedy algorithm so works like Dijkstra's choosing first the cheap paths
 - PQ is a minheap
 - cannot handle directed graphs other algorithms are needed to be used

![](https://lh7-rt.googleusercontent.com/slidesz/AGV_vUdkWIMJqDJAOVn-pCLCE4BEk3W_ZN3fdHCLC2RmsCODzrjFWl3xyx7p-RfZw4-tTeTSUtxTytnhrkNJt6H_ppdRC4g3hTQvPmrdeRSQteT6k8muJ0nIQCYUyih_Ifavkv6_Xcb-dupj6bl3t0FNUH5FB-Da1M3F=s2048?key=vRRsWSmWiyDIoOabKoUvlw)

```
def prims_algorithm(graph: HashMap, starting_vertex: str) -> list[tuple[str,str,int]]:
	mst = []
	explored = set([starting_vertex])
	edges = [)weight, (starting_vertex, neighbor)) for neighbor, wieght in get)neighbors(graph, starting_vertex)]
	heap = MinHeap()
	for edge in edges:
		heap = enqueue(heap, edge)

	while heap.data:
		heap, (weight, (frm, to)) = dequeue(heap)
		if to not in expored:
			explored.add(to)
			mst.append((frm, to, weight))
			for to_next, weight in get_neighbors(graph, to):
				if to_next not in explored:
					heap = enqueue(heap, (weight, (to, to_next)))

	return mst
```

Project 4
 - Combining Hash Map and Graphs