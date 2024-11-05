10/28/2024

[Slideshow Link](https://docs.google.com/presentation/d/1iS4t1ILN0lo4Jj8AnQ67T3W_JqjobuVC60duU7nq3e8/edit#slide=id.g2ce5d65a0db_0_308)

Priority Queue ADT
 - similar to the queue but with an added feature
 - each element is given a priority
 - calling it a priority queue but underneath the engine it is really just a heap
 - elements are added to the end but removed based on priority
 - uses heapify up to order the elements
 - enqueue(heap insert operation) and dequeue(heap extract operation)
 - time complexity for enqueue is going to then be $O(log(n))$ and dequeue as well

Project 3: Binary Heap of Nodes
 - min-heap of nodes, priority is lowest number accompanying a letter
 - removes elements based on frequency and uses letters to break ties
 - PQ = [(A, 1), (B, 2), (C, 3), (D, 3)]
 - enqueue and dequeue are just wrappers for insert and extract

```
from dataclasses import dataclass

@dataclass(order=Ture, frozen=True)
class Node:
	freq: int
	char: str
	left: Node | None = None
	right: Node | None = None
```

Applications
 - CPU Scheduling ram/cache handling
 - graph algorithms
 - Huffman encoding

Huffman Encoding
 - lossless data compression algorithm
 - based on likelihood of number/letters
 - assigns variable-length codes to input characters based on their frequencies
 - "ABRACADABRA" length 11 each char is 1 byte so 88 bits
	 - with encoding is encrypted by "01101001110011110110100" as 23 bits
 - is important for streaming and download times

Building the Huffman Tree
 - dequeue twice first the left then the right

```
PQ = (C1, D1, 2B, 2R, 5A)

DQ = (C1, D1) -> Node(2, C, left = C1, right = D1) #takes lowest char

NQ(Node())
PQ = (2B, 2C, 2R, 5A)

DQ (2B, 2C) -> Node(4, B, left = 2B, right = 2C)

NQ(Node())
PQ = (2R, 4B, 5A)

DQ = (2R, 4B) -> Node(6, B, left = 2R, right = 4B)

NQ(Node())
PQ = (5A, 6B)

DQ = (5A, 6B) -> Node(11, A, left = 5A, right = 6B)

NQ(Node())
PQ = (11A)

#now at one element creates tree based on how it got to the element

Huffman Tree

     A11
      
  /       \

A5         B6   

       /        \

    R2           B4

              /       \

            B2          C2

                     /    \

                  C1         D1

```

Huffman Encoding
 - done via depth first search, traverse until reach a leaf node
 - 0 represents right 1 represents left

```
A: L -> 0
R: R, L -> 10
C: R, R, L -> 110
D: R, R, R, L -> 1110
R: R, R, R, R -> 1111

therefor ABRACADABRA is 
0 110 10 0 1110 0 1111 0 110 10 0
```

Huffman Decoding
 - Key is the Huffman Tree, needed for the characters, capture each character and then translate

Example 

```
puppets
p = 3
u = 1
e = 1
t = 1
s = 1
PQ = (e1, s1, t1, u1, p3)

DQ = (e1, s1) -> Node(2, e, left = e1, right = s1)

NQ(Node())
PQ = (t1, u1, e2, p3)

DQ = (t1, u1) -> Node(2, t, left = t1, right = u1)

NQ(Node())
PQ = (e2, t2, p3)

DQ = (e2, t2) -> Node(4, e, left = e2, right = t2)

NQ(Node())
PQ = (p3, e4) -> Node(7, e, left = p3, right = e4)


Huffman Tree

              e7
	       /      \
	     p3         e4
	              /    \
	            e2       t2
			  /    \    /   \
			e1     s1  t1   u1  

Huffman Encoding is
0 111 0 0 100 110 101
```

```
kittens
t = 2
k = 1
i = 1
n = 1
e = 1
s = 1

Q = [e1, i1, k1, n1, s1, t2]

DQ = (e1, i1) Node(e2, left = e1, right = i1)

NQ = [k1, n1, s1, e2, t2]

DQ = (k1, n1) Node(k2, left = k1, right = n1)

NQ = [s1, e2, k2, t2]

DQ = (s1, e2) Node(e3, left = s1, right = e2)

NQ = [k2, t2, e3]

DQ = (k2, t2) Node(k4, left = k2, right = t2)

NQ = [e3, k4]

DQ = (e3, k4) Node(e7, left = e3, right = k4)

Huffman encoding

			 e7
		 /        \
		e3.        k4
	   /  \       /   \
	  s1   e2    k2    t2
	      /  \  /   \   
	     e1  i1 k1  n1 

so final encoding is
100 011 11 11 010 101 00
```