	11/04/2024

[Slideshow Link](https://docs.google.com/presentation/d/1k2ZIHYhy_3S4DhDjI5NB2Nd1joW6wfMK2mwUWUjV31A/edit#slide=id.g26f23fb6c32_0_245)

Separate Chaining
 - collision resolution uses linked lists(or buckets) where each index is now a bucket that can store multiple groups of data
 - now when there is a collision data is appended to the data structure
 - does not need to be an linked list, can be any data structures
 - advantages are that it is simple to implement, performance is good even with a high load factor especially if each list is short, it also is very flexible
 - downsides are increased memory usage

```
data: list[list[int]]
```

Separate Chaining Retrieval
 - you need to search the bucket to retrieve an element that you are looking for
 - this ruins the time complexity as sometimes is is $O(1)$ but then when retrieving from a collision bucket it is $O(n)$ 
 - deletion also requires this search

Open Addressing
 - through probing a new spot in the index array is chosen

Linear Probing
 - find the next available slot going by one each time
 - efficient memory usage
 - to retrieve match the key after trying the index
 - to delete you need to use a tombstone, set to 10000 signifying a index has been deleted
 - delete passes over the tombstones
 - runs into a clustering issue, fills spaces that otherwise would have just been $O(1)$ leads to time complexity of $O(n)$ 

Quadratic Probing
 - same as linear probing but instead of searching following 1 2 3 4 5 so on it does 1 4 9 16 25 or $n^2$ indexing
 - this helps avoid the clustering issue of linear probing
 - leads to secondary clusters that initially helped the primary cluster this is due to the same indexing pattern

Double Hashing
  - utilizes two hash functions to produce a custom step size for each key to index by to help avoid clustering 
  - sets index counter to 0 and then if a collision occurs you use secondary_hash to calculate a step size that is then multiplied by index counter and the tried through the primary_hash to find available space
  - retrieval is kinda a pain needs to backtrack a lot
  - clusters is minimized, because of improved distribution
  - more complex

```
def primary_hash(key: int, dcapacity: int) -> int:
	return key % capacity

def secondary_hash(key: int, capacity: int) -> int:
	return 1 + (key %(capacity -1))
```

Time Complexity
 - all regardless of collisions have a time complexity of $O(n)$ because of their worst case complexities
 - so what to chose? 
	 - separate chaining is good for high load factors and uneven key distributions
	 - linear probing is good for low load factors and simplicity
	 - quadratic probing is good for when clusters appear in linear probing
	 - double hashing is good for high when both linear and quadratic don't work