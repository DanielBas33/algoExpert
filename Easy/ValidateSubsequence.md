# Validate Subsequence

### Understanding the problem

Given two non-empty arrays of integers I am asked to code a function that determines whether the second array is a subsequence of the first one.

A subsequence of an array is a set of numbers that aren't necessarily adjancent in the array but that are in the same order as they appear in the array.

Ex: [1,3,4] is a subsequence of [1,2,3,4] but [2,1,3,4] is not.

#

### Approach 1: While loop

We know that the order is important for the sequence to be a subsequence so basically we are going to look one by one for each of the elements of the sequence inside of the array. 

In this first approach we use a pointer in each of the arrays. We loop through the original array on each iteration looking for a match with the sequence's current number. When or if we find a match we then add one to the sequence pointer and continue iterating through the array. So if array[arrIdx] is equal to sequence[seqIdx] we will do seqIdx += 1 and arrIdx += 1 but if not we just do arrIdx += 1. This way we make sure the values are in the same order. At the end only if the seqIdx is equal to the lenght of the sequence we know that we have a subsequence.


### Implementation

```python
def isValidSubsequence(array, sequence):
	seqIdx = 0
	arrIdx = 0
    while arrIdx < len(array) and seqIdx < len(sequence):
		if array[arrIdx] == sequence[seqIdx]:
			seqIdx += 1
		arrIdx += 1
    return seqIdx == len(sequence)

```

### Complexity Analysis

- Time Complexity: O(N), where N is the number of integers in the input array.

- Space Complexity: O(1). No additional space

#

### Approach 2: For loop

As we learned on the first approach the only relevant pointer to have would be the sequence pointer so we can just use a foor loop to iterate throgh the array and similarly to the first approach add 1 to the sequence index every time we have a match. If we get to the end of the sequence we will also break the for loop.

This approach has the same time and space complexities, it is just a different way to approach the problem.

### Implementation

```python
def isValidSubsequence(array, sequence):
	indexSeq = 0
	for number in array:
		if sequence[indexSeq] == number:
			indexSeq += 1
		if indexSeq == len(sequence):
			break
	return indexSeq == len(sequence)
```

### Complexity Analysis

- Time Complexity: O(N), where N is the number of integers in the input array.

- Space Complexity: O(1). No additional space.

#