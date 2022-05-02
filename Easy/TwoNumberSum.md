# Two Number Sum

### Understanding the problem

Given a non-empty array of distinct integers and a target sum I am asked to code a function that will check if two numbers on the array add up to the target sum. If so the function will return an array of those numbers and if not it will return an empty array.

Note: Any given number can only be used once, we cannot just add twice the same number.

This question is the first of a list of similar questions like the three and four number sums, it is the easiest but it will teach us how to approach the harder ones.

#


### Approach 1: Two for loops

The first thing that may come to mind is to use two for loops. On the second loop check if any number sums up to the target with the first loop iteration. This would work but it is the worst of the approaches as it will have a time complexity of N^2 which is pretty bad.

### Implementation

```python
def twoNumberSum(array, targetSum):
    for i in range(len(array) - 1):
		firstNum = array[i]
		for j in range(i + 1, len(array)):
			secondNum = array[j]
			if firstNum + secondNum == targetSum:
				return [firstNum,secondNum]
    return []

```

### Complexity Analysis

- Time Complexity: O(N^2), where N is the number of integers in the input array.

- Space Complexity: O(1).

#

### Approach 2: Hash table

By using a hash table we can traverse only once through the array checking in the hash table for a number that sums up to the target with the current iteration number in the array. If there is no match we add the number to the hash table and iterate to the next number in the array. This way the time complexity will be much better as there will only be one for loop. The only problem is that as we are using more space the space complexity will be O(N) because of the hash table. Hash table access is constant, thats why the new time complexity will be O(N).

### Implementation

```python
def twoNumberSum(array, targetSum):
	nums = {}
	for num in array:
		potentialMatch = targetSum - num
		if potentialMatch in nums:
			return [potentialMatch,num]
		else:
			nums[num] = True
    return []
```

### Complexity Analysis

- Time Complexity: O(N), where N is the number of integers in the input array.

- Space Complexity: O(N). We use the same array that we were given but we also use the hash table.

#

### Approach 3: Sort

This last approach uses sorting the array to reduce the number of loops to one. First we sort the array as mentioned. We then point to the start and end of the array with two pointers which we can call L and R. We then add up those two numbers and compare the sum to the target. If the result is smaller than the target then we move the L pointer to the next value and if the result is bigger than the target we move the R pointer to the previous number. This only applies because the array is sorted and we know that the L pointer is the smaller number and the R pointer the larger number.

Sorting makes the time complexity O(nlog(n)) which is worse than the hash table approach but the space complexity goes back to O(1) so it all depends on what we are looking for on the approach.

### Implementation

```python
def twoNumberSum(array, targetSum):
    array.sort()
	left = 0
	right = len(array) - 1
	while left < right:
		currentSum = array[left] + array[right]
		if currentSum == targetSum:
			return [array[left],array[right]]
		if currentSum > targetSum:
			right -= 1
		if currentSum < targetSum:
			left += 1
    return []
```

### Complexity Analysis

- Time Complexity: O(nlog(n)), where N is the number of integers in the input array. We only use one loop but sorting has a time complexity of O(nlog(n)). 

- Space Complexity: O(1). We use the same array that we were given.

#
