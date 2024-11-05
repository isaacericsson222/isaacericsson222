10/30/2024

[Slideshow Link](https://docs.google.com/presentation/d/18NkVCpWIKnFpv_BASXDekt63Oh0IEkR-w7oEE-wIJSY/edit#slide=id.g26f244675b2_0_237)

Keyed Data Structures
 - Map (java), Dictionary (python), and Associative Array(C++)
 - stores data in key-value pairs possibly $O(1)$ 
 - dynamic sizing

Dictionary
 - access a value using a unique key
 - how is this possible?
 
```
fruit_prices = {'apple': 0.99, 'banana': 0.49, 'orange': 0.79}

print("the price of an apple is $, fruit_prices['apple'])
```

Hashing
 - uses a hash function to "hash" or convert keys to index values
 - an actual hash table is an array that takes these index values
 - collisions are when two different keys produce the same index after hashing, they are vying both for the same slot, caused by either the hash function or having identical keys

Hash Function
 - takes a key and outputs an integer
 - should have uniform distribution spreading keys evenly across the table

```
def simple_hash(value: int, capacity:int) -> int:
	return value % capacity
```

Simple Dictionary
 - fixed size hash map

```
@dataclass(frozen=True)
class HashMap:
	capacity: int
	data: list[int] = field(default_factory=list)

	def __post_init__(self):
		if len(self.data) > self.capacity:
			raise ValueError("Data exceeds capacity")

		object.__setattr__(self, 'data', self.data + [None] * (self.capacity - len(self.data)))	
```

Insert
 - provide hash-map and value then find a place and store the value

```
def insert(hash_map: HashMap, value: int) -> HashMap:
	index hash(value, hash_map.capacity)

	if hash_map.data[index] is not None:
		raise ValueError(f"Collission at index {index})

	new_data = hash_map.data[:]
	new_data[index] = value

	return HashMap(capacity=hash_map.capacity, data=new_data)
```

Retrieval
 - Assume it is already stored otherwise return None

```
def get(hash_map: HashMap, key: int) ->
	index = hash(key, hash_map.capacity)

	value = hash_map.data[index]

	if value is None:
		return None

	else:
		return value
```

Deletion
 - Remove values, check for existing values, return a copy (immutability)

```
def delete(hash_map: HashMap, key: int) -> HashMap:
	index = hash(key, hash_)map.capacity)

	if hash_map.data[index] is NOne:
		raise ValueError(f"No value found at key {key} to delete.")

	new_data = hash_map.data[:]
	new_data[index] = None

	return HashMap(capacity = hash_map, data = new_data)
```

Results of Simple Hash
 - Has many collisions, we will see next lecture how to resolve these issues
 - one solution is to use a massive amount of space doesn't guarantee no collisions