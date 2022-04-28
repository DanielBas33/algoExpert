# Selection Sort

### Understanding the problem

Given an array of integers, I am asked to write a function that uses Selection Sort algorithm to sort the array and returns it.

#


### Approach 

The selection sort is one of many sorting algorithms and although it is not the most eficient it does the job and it is easy to understand and implement. To implement it we will create a space at the beginning of the array which will be our sorted array. Then we will iterate through the array and we will insert the smallest number to the sorted array on each iteration.

Example:

Starting point: unsorted

array = `[8,5,2,9,5,6,3]`

Step 1: swap 2 and 8

array = `[2,5,8,9,5,6,3]`

Step 2: swap 3 and 5

array = `[2,3,8,9,5,6,5]`

Step 3: swap 8 and 5

array = `[2,3,5,9,8,6,5]`

...

Final array: sorted

array = `[2,3,5,5,6,8,9]`

On each iteration we insert the smallest number from the array to the sorted array until every number is on the sorted array.


### Implementation

```python
def selectionSort(array):
    currentIdx = 0
	while currentIdx < len(array) - 1:
		smallestIdx = currentIdx
		for i in range(currentIdx + 1, len(array)):
			if array[i] < array[smallestIdx]:
				smallestIdx = i
		swap(smallestIdx, currentIdx, array)
		currentIdx += 1
	
    return array

def swap(i, j, array):
	array[i], array[j] = array[j], array[i]
```

### Complexity Analysis

- Time Complexity: O(N^2), where N is the number of integers in the input array.

- Space Complexity: O(1). We use the same array that we were given by just swaping some numbers.

#
