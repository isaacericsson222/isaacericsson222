
![[Midterm 2.pdf]]

1.
Both b) and d) are valid binary search trees

2.
I = [45, 12, 3, 2, 6, 0, 50, 9, 2, 1]

S

3.
resize at 3 full
[24, None, 6, 19]
[24, None, None, 19, None, None, 6, 7] 

4.
Done by hand

5.Function that adds two bsts node by node
```
@dataclass(frozen=True) 
class Node: 
value: int 
left: 'Node' | None = None 
right: 'Node' | None = None

def add_trees(bst1: Node | None, bst2: Node | None) -> Node | None:

	P
	return Node(bst1.value + bst2.value, left = add_trees(bst1.left, bst2.left), right = add_trees(bst1.right, bst2.right))
	
```

6.
a) example would be a tree where target is one to the right and long path
b) example would be tree where target is down a long path 
c) just a different order for the tree

7.getters
a) 100 01 11 11 01 101 00
b)moonbeam
c)aggregate
```
PQ = [r1, t1, a2, e2, g3]
DQ [r1, t1] Node(r2, left = r1, right = t1)
PQ = [a2, e2, r2, g3]
DQ [a2, e2] Node (a4, left = a2, right = e2)
PQ = [r2, g3, a4]
DQ [r2, g3] Node (g5, left = r2, right = g3)
PQ = [a4, g5]
DQ [a9] Node (a9, left = a4, right = g5)


						a9
				     /      \
				   a4.       g5
			 .  /.   \.     /.  \
			   a2.    e2.   r2.   g3
			              /.   \ 
			            r1      t1

final encoding is 
00 11 11 100 01 11 00 101 01
			 
```