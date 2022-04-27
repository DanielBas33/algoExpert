# Binary Search

### Understanding the problem

Given a sorted array of integers and a target integer, I am asked to write a function that uses Binary Search algorithm to find out if the target integer is in the array. If the target is in the array, the function should return its index, otherwise return `-1`.

#

### Approach 1: Iterative

The Binary Search algorithm works by dividing the search space into halves, and based on the value of the middle element, it eliminates half of the search space.

We maintain two pointers `left` and `right` that are going to define the current search space. Initially, the search space is the entire list. We find the middle value using the two pointers and compare it to the search target. If the middle value is equal to the target value, we've found the target. If the middle value is greater than the target, then it means the target value cannot lie in the right half of the search space. Because the list is sorted, all the values that come after the middle value must be greater than the middle value and even greater than the target, so we can remove the entire right half, narrowing down the search space to the left half. If the middle value is smaller than the target, then we can discard the entire left half and search for the target value in the right half. We repeat this process until the target value is found, or our search space is exhausted.

### Implementation

```python
def binarySearch(array, target):
    leftIdx = 0
	rightIdx = len(array) - 1
    
	while leftIdx <= rightIdx:
		middleIdx = (leftIdx + rightIdx) //2
		if array[middleIdx] == target:
			return middleIdx
		elif array[middleIdx] < target:
			leftIdx = middleIdx + 1
		elif array[middleIdx] > target:
			rightIdx = middleIdx - 1
	return -1
```

### Complexity Analysis

- Time Complexity: O(log(N)), where N is the number of integers in the input array.

- Space Complexity: O(1).

#

### Approach 2: Recursive

We are going to define a recursive function that is going to take in the input array, the search target and two pointers `left` and `right` as parameters. We find the middle value using the two pointers and compare it to the search target. We then recurse either on the left half or on the right half based on the result of comparison. The recursion stops when the target is found or the `left` pointer surpasses the `right` pointer.

### Implementation

```python
def binarySearch(array, target):
    return binarySearchHelper(array, target, 0, len(array) - 1)

def binarySearchHelper(array, target, left, right):
	middle = (left + right) //2
	if left > right:
		return -1
	elif array[middle] == target:
		return middle
	elif array[middle] < target:
		return binarySearchHelper(array, target, middle + 1, right)
	else:
		return binarySearchHelper(array, target, left , middle - 1)

```

### Complexity Analysis

- Time Complexity: O(log(N)), where N is the number of integers in the input array.

- Space Complexity: O(log(N)) to keep the recursion stack.

#

