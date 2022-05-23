# Find Three Largest Numbers

### Understanding the problem

Given an array of at least three integers return a sorted array of the three largest integers on the input array. 

Note: You cannot sort the input array.

#

### Approach 

This problem is more tricky that it may seem at first. To solve it we will need to iterate through the array. Create an output array with three None values and compare on each iteration to swap integers until we have the final result array. We will compare from last to first on the result array as we want the solution to be sorted, if the current iteration value is bigger than the last value in the result array we will swap those and move every integer on the result array one position backwards, removing the first number on the array. The time complexity of this will be O(n) since we need to traverse the entire input array. We also traverse our output array but since we know the array will store 3 values this will be done in constant time. For the space we also only store this three values so it will be O(1).


### Implementation

```python
def findThreeLargestNumbers(array):
    threeLargest = [None, None, None]
	
	for number in array:
		if threeLargest[2] is None or threeLargest[2] < number:
			swap(2, threeLargest, number)
		elif threeLargest[1] is None or threeLargest[1] < number:
			swap(1, threeLargest, number) 
		elif threeLargest[0] is None or threeLargest[0] < number:
			swap(0, threeLargest, number) 
			
	return threeLargest
			
def swap(index, array, number):
	
	for i in range(index + 1):
		if i == index:
			array[i] = number
		else:
			array[i] = array[i + 1]
```

### Complexity Analysis

- Time Complexity: O(n), where n is the length of the input array.

- Space Complexity: O(1). There is a new array used but it will we now it has three values so at the end it is constant space.

#
