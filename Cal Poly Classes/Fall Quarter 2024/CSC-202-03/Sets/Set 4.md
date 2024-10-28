10/21/2024
[Set 4](https://canvas.calpoly.edu/courses/137532/assignments/1102905)

Mostly done by hand


7.
```
def merge_queue(q1: queue, q2: queue, nq: queue | None = None) -> queue:
	if q1.capcity > q2.capacity:
		nq = [None] * 2 * q1.capacity
		for i in range nq.capacity:
			nq[i] = q1[i]
			nq[i + 1] = q2[i]
			i + 1

	elif q2.capcity >= q1.capacity:
		nq = [None] * 2 * q2.capacity
		for i in range nq.capacity:
			nq[i] = q1[i]
			nq[i + 1] = q2[i]
			i + 1

return nq
```