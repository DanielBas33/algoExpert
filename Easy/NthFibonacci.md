# Nth Fibonacci

### Understanding the problem

The Fibonacci sequence is defined as folllows: the first number of the sequence is 0, the second number is 1, and the nth number is the sum of the (n-1)th and the (n-2)th numbers. 

We are asked to write a function that takes an integer n and returns the nth Fibonacci number.

NOTE: In this exercise the result of n = 1 is 0 and the result of n = 2 is 1. 

#

### Approach 

This problem is easily solved through recursion. The value we will return will consist of calling the same function on n-1 and n-2 and sum those values. Apart from that we will add to conditions that will instead return 0 or 1 if n is equal to 1 or 2 as we noted on the above explanation.

### Implementation

```python
def getNthFib(n):
	
	if n == 1:
		return 0
	if n == 2:
		return 1
		
    return getNthFib(n-1)+getNthFib(n-2)
```

### Complexity Analysis

- Time Complexity: O(2^n), each time we call the function it calls itself two more times. So the function is called 2*2*2... until we do it n times.

- Space Complexity: O(n), because of the call stack.

#
