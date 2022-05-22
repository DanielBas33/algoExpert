# Product Sum

### Understanding the problem

Given a "special" array return its product sum. A "special" arrayt is a non-empty array that contains either integers or other "special" arrays. 
The product sum is the sum of its elements where the arrays inside are also summed and multiplied by their level of depth.

Example:<br/>
`[x,y]` The product sum is x + y <br/>
`[x,y,[z,c]]` The product sum is x + y + 2 * (x + c)

#

### Approach 

To solve this problem we can use recursion by calling the productSum function when we reach a list inside the array. We can store the current multiplier or depth and return the sum of the values multiplied by this number. This solution would need to store the current values on the stack so we will have a space complexity of O(d), where d is the max depth the stack will reach and also de max depth of a special array in our initial array. For time complexity we willk have O(n) where n is just the number of elements including sub-elements.

### Implementation

```python
def productSum(array, multiplier = 1):
	totalSum = 0
	for element in array:
		if type(element) is list:
			totalSum += productSum(element, multiplier + 1)
		else:
			totalSum += element
	return totalSum * multiplier
```

### Complexity Analysis

- Time Complexity: O(n), where m is the total number of elements in the aray, including sub-elements.

- Space Complexity: O(d), where d is the max depth of the array.

#
