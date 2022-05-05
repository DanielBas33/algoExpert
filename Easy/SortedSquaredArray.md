# Sorted Squared Array

### Understanding the problem

Given an array of sorted integers return a NEW array with the squares of those integers also sorted.

Ex: [1,3,4] would return [1,9,16].

Note: take care of negative values.

#

### Approach 1: Brute force

The first solution that may come to mind is to brute force the problem. By this I mean we could just traverse through the original array while creating a new array with the squares of the first one. After doing this we could use a sorting function and we would have the correct result. The only issue with this approach is time complexity. As we know sorting will have at best a time complexity of O(nlog(n)).


### Implementation

```python
def sortedSquaredArray(array):
	result = []
	for number in array:
		result.append(number**2)
	result.sort()
    return result
```

### Complexity Analysis

- Time Complexity:  O(nlog(n)). Actually its N + nlog(n) but nlog(n) is bigger so that would be the time complexity.

- Space Complexity: O(N). We create an entire new array.

#

### Approach 2: 

Whenever we are given a sorted array to solve a problem this should give as a hint that maybe the problem could be solved in linear time.

We know that the largest squared value is going to be at the beginning or the end of the input array so we are going to compare the absolute value of this two pointers and place the square of the larger one at the end of the new array. If the bigger value is the pointer at the start we add one to it and if it is the one at the end we substract one from it. Repeat this until we have the solution.

For this approach we will need to create a newArray with the same length as the input one and fill it with zeros so that we can then insert the squared values. 

### Implementation

```python
def sortedSquaredArray(array):
	newArray = [0 for _ in array]
    smallest = 0
	biggest = len(array) - 1
	for i in reversed(range(len(array))):
		if abs(array[smallest]) > abs(array[biggest]):
			newArray[i] = array[smallest]**2
			smallest +=1 
		else:
			newArray[i] = array[biggest]**2
			biggest -= 1
			
    return newArray
```

### Complexity Analysis

- Time Complexity: O(N). Time here is O(N) because we are just iterating through the array with no extra steps.

- Space Complexity: O(N). Pointers are constant space so we have the same space complexity as the first approach.

#