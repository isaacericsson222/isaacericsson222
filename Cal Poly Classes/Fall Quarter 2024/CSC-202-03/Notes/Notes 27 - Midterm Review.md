12/06/2024

Types and Annotations
 - TypeAlias exam uses different format
 - Number: TypeAlias = Union[int, float] means int | float
 - OptionalString: TypeAlias = Optional[str] means str | None

Data Definition
 - What types and classes you will use to represent data
 - no need to create functions etc

Asymptotic Analysis
 - make sure you know which time complexity beats what
 - remember Big Theta representing a tight bound because both best and lower case are the same, the average case
 - be comfortable with time estimates T2 = T1 * (n2 / n1) or T2 = T1 * ((n2 / n1)^2) or T2 = T1 * (log(n2) / log(n1))

Linked List
 - use cases and time complexity
 - O(n) for all operations
 - frozen = True
 - be able to write insert, reverse a linked list

Stacks
 - LIFO principle
 - push, pop, peek
 - O(1) complexity when

Queue
 - FIFO principle
 - O(1) complexity when
 - know different implementations (reversed, linked list, two stack)

Priority Queue
 - min heap or max heap
 - main use is Huffman encoding on final

BST Property
 - remember the property and that all subtrees must follow
 - look back on preorder, postorder, and inorder
 - BFS DFS
 - time complexity is O(1) O(log(n)) O(n))

Heaps
 - work with the list representation and the tree representation
 - children are at 2i + 1 and 2i + 2
 - heapify up heapify up, sift up sift down

Heapify
 - to adjust after insertion or deletion
 - Bubble up, Sift Up
 - compares with parent, and swaps if needed
 - continue until restored or root is reached
 - Bubble, Sift Down
 - extracting element
 - move last element to the root and then compare the children, swap with smallest child until heap property is restored

Hash Table
 - be comfortable making your own and arguing for them about collisions
 - know how to resolve the collisions