11/06/2024

[Slideshow Link](https://docs.google.com/presentation/d/1M9YOSH-vZV8dqmVy_luXacqgraEJAV0OrH_KaCl1Q60/edit#slide=id.g26f1a35504f_0_166)

Polynomial hash Function
 - with large hash tables these calculations can become computationally expensive
 - results in no collisions 

Perfect Hash Functions
 - guarantee a $O(1)$ time complexity with no collisions
 - usually only works for one data set

Rehashing
 - expanding the hash table by resizing the hash table, reduces collision occurrences by increasing the size
 - load factor $(\lambda)$ indicates how full a hash table is a ratio of number of stored entries to total entries
 - a lower load factor reduces space efficiency but improves access speed by reducing collisions
 - manage load factor by resizing every time the load factor threshold is crossed, this lets you maintain a load factor beneath a certain amount this is called the trigger point
 - typically resizes to twice as large
 - time complexity is $O(1)$ amortized because rehash is $O(n)$ however only used to then reduce collisions resulting in the amortized value

```
def rehash(hash_map: HashMap, new_capacity: int) -> HashMap:
	new_data = [None] * new_capacity
	for item in hash_map.data:
		if item is not None:
			index = hash(item) % new_capacity

			while new_data[index] is not None:
				index = (index + 1) % new_capacity
				
			new_data[index] = item
```

Optimal Load Factor
 - a common rule of thumb is to resize when the load factor exceeds 0.7 because it is found that this is generally the best for collisions and load factor $(\lambda)$ 

Pythons Dictionary
 - holds any data
 - uses a different hash function depending on the keys used
 - uses linear probing until collisions are detected, uses a 1.2 factor to resize
 - time complexity for language hash tables are $O(1)$ 

Real World Applications
 - used heavily in cryptography, mining resolves hash puzzles
 - heavy fines for saving things in plaintext, that then get leaked and credentials get ruined
 - coding interviews are a lot about data structure algorithms