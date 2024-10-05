10/2/2024

[Slideshow Link](https://docs.google.com/presentation/d/1lKso0LivCzTlT36f5o0hFIDT_nhZFQT7RnTogD1dYXk/edit?usp=sharing)

**Algorithm Analysis**

Time Complexity
 - how the execution time of a program increases with different inputs

AKA
 - Algorithm complexity, Big O, Run-time Efficiency

Space Complexity
 - Memory usage of an algorithm
 - Not going to be focused on


Time Complexity
 - A way to quantify the time length of a function based on an nput
 - Best case with the minimum number of operations
 - Average case, and Worst case
 - Think of a linear search function, best case is findNum is start of the list, worst case it's at the end

Big $O$ notation - Upper Bound
 - $f(n)\  is\  O(g(n))$ if there exists constants c > 0 and $n_0 \ge 0$ such that for all $n \ge n_0$, we have $f(n) \le c * g(n)$
 - Helps predict the worst case scenario
 - For linear search for n input there is n operations therefor it is $O(n)$
 - $O(1)$ is best case scenario, a single operation
 - $O(2^n)$ and $O(n!)$ are the worst possible ones that can take your lifetime and more to complete

Big  $\Omega$ (Omega) notation - Lower Bound
 - Lower bound, minimum time an algorithm will take
 - never gets better
 - In this linear search function the best case is the number you are searching for is at the start of the list therefor it is $\Omega (1)$

Big $\Theta$ (Theta) notation - Tight Bound
 - Represents an upper and lower bound
 - Functions don't always have a $\Theta$ because some don't have a lower bound
 - $f1(n) = 3n^2$ is $O(n^2)$ and $\Omega(n^2)$ therefor $\Theta$ is also $\Theta(n^2)$

Reflexivity in Asymptotic Growth
 - A function belongs to the set of functions that do not grow faster than itself

Transitivity in Asymptotic Growth
 - Establishes a hierarchy of function growth rates
 - Helps with understanding how fast functions perform

Sum of Functions in Asymptotic Growth
 - The sum of two functions with the same time complexity stay in the same time complexity (adding constants)
 - Adding a function with a higher time complexity to one that is lower creates a function that takes on the complexity of the higher time complexity

How to Calculate Time Complexity
 - Single loops from 1 to 'n' represent $O(n)$
 - Nested Loops multiply and result in $O(n^2)$
 - Binary searches cut the search in half each loop resulting in a $O(log(n))$
 - Some things that can change this include a single loop that exponentially increments (while i < n: i *=2)
 - Early exits can reduce real runtime, but don't usually change the time complexity

Nested loop with strings example (Complexity of $O(n^2)$)
```
def print_string_combinations(strings: list[str]) -> None:
    # Outer loop to select the first string
    for s1 in strings:
        # Inner loop to select the second string and combine it with the first
        for s2 in strings:
            # Print the concatenated result of the two strings
            print(s1 + s2)
  
# Example usage:
string_list = ["apple", "banana", "cherry"]
print_string_combinations(string_list)
```

Analyzing Recursion
 - Same application, treat it as a loop, nested recursive cases result in higher time complexities
 - Last lab we had a recursive function that halved a list, this was a recursive function with the time complexity of $O(log(n))$
 - Our Fibonacci function was a display of a recursive function with time complexity of $O(2^n)$

Estimating Time Performance
- A function take 1 second for 1000 elements and is $O(n)$ and therefor linear
- for 10,000 elements it would take approximately 10 seconds
- $Time = K * Input$ (for previous example $1 = K * 1000$)
- An algorithm with $O(n^2)$ processes 100 elements in 1 second and is not linear
- for 1000 elements it would take 100 seconds (since $1,000^2 / 100^2 = 100$)
- This is only a time estimate!

Measuring Performance
 - Python Tools include 
	 -  time module: time module for measuring execution time, problems include computer, language, and compiler
```
import time
start_time = time.perf_counter()
i = 0 
for n in range(100000):
	i = n 
end_time = time.perf_counter()
print(f"Execution time: {end_time - start_time} seconds")

#Execution time: 0.00881212200000192 seconds
```