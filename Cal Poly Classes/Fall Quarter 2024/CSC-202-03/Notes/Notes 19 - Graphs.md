11/08/2024

[Slideshow Link](https://docs.google.com/presentation/d/1ZHvOKLUBkTIS6QfoaHTTFl9_hR4dpW1lCJXseGs3Cwc/edit#slide=id.g26f241fdd8f_0_296)

Graphs
 - an ordered pair of vertices and edges(or links)
 - lots of applications, social networks, internet connectivity, geographical maps

Graph ADT
 - Vertices with edges to neighbors
 - add vertex/edge
 - remove vertex/edge
 - find vertex/edge
 - get adjacent vertices

Graphs are Not Trees(but trees are graphs)
 - cyclic vs. acyclic
 - graphs don't have a root
 - graphs can have multiple paths between nodes

Undirected Graphs
 - edges between nodes have no direction
 - each edge is bidirectional allowing movement in both direction between anay two connected nodes

Directed Graphs
 - each edge has a specific direction, they are one way

Adjacency in Graphs
 - adjacency is the nodes reachable from a vertex
 - uses the term neighbors to represent adjacency
 - easy in unidirectional graphs, for directional ones you must determine the path of the edges

Degree of a Vertex
 - number of edges connected to a node
 - for directed graphs there are in-degree and out-degree for the number of edges going into the vertex and number that are going out of the vertex

Loops
 - a node connected to itself
 - does increase in/out degree

Paths in Graphs
 - a path is defined as at least 3 nodes long(otherwise it is just an edge)
 - can be lots in a graph
 - weights can change this

Cycles
 - a closed path, same minimum of 3 vertices
 - no repeats
 - cyclic graph contains at least one cycle, acyclic graph contains none (trees)

Connected Component
 - one large graph does not necessarily have all components connected
 - this image is technically one large graph with 4 sub graphs that are not connected
 
**![](https://lh7-rt.googleusercontent.com/slidesz/AGV_vUeOsO4n4JoQDTMqaQfscZC3X_W3J4HxCd_eafr0EGnT2jb2Ho_Wd96M07WAONH9AaF5DWk3iqtA6k8mS_IX0fbExlj0D7tk47Jkau0mEOA-CS3A8YRP_OMagOl5FlCOnWxvHss5C_ZakmKw76wscZBP-Am8pcw=s2048?key=4IEhGZXmxF7fxeo6SGzlZA)


Graph Representation Overview
 - use an adjacency list

```
class Node:
	value: any
	neighbors: list[Nodes[]] = []
```

Adjacency List
 - a collection of lists or arrays used to represent a finite graph
 - for each vertex there is a list of vertices which it is directly connected to
 - 'B': [A, C, D] 
 - convenient because if you look at a node you can grab all of it's neighbors
 - less convenient to delete vertices because you then have to navigate through each node list
 - better for graphs that are constantly updated, like social networks, or transportation networks

Adjacency Matrix
 - uses a graph to represent a finite graph using 0 for no edge, and 1 for edge
 - good for dense graphs
 - uses a constant time complexity of $O(1)$ to lookup the presence of an edge
 - uses more memory
 - better for network flow algorithms

A is connected to B and C and F
B is connected to A and C
C is connected to A and B and D and E
D is connected to C and E
E is connected to C and D and F
F is connected to A and E

Resulting Adj_Matrix: (note the ABCDEF columns are not usually labeled)
  A B C D E F
A[0,1,1,0,0,1]
B[1,0,1,0,0,0]
C[1,1,0,1,1,0]
D[0,0,1,0,1,0]
E[0,0,1,1,0,1]
F[1,0,0,0,1,0]

Counting Indegree
 - counting how many neighbors flow into a vertices
 - for adjacency list, try each one and iterate through then add 1 per path found

```
def get)indegrees(adjacency_list):
	indegrees = {}

	for neighbors in adjacency_list.values():
		for neighbor in neighbors:
			if neighbor in indegrees:
				indegrees[neighbor] += 1
			else:
				indegrees[neighbor] = 1

	return indegrees
```