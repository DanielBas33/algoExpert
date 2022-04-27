# Bubble Sort

### Understanding the problem

Given an array of integers, I am asked to write a function that uses Bubble Sort algorithm to sort the array and return it.

#


### Approach 1

The bubble sort is one of many sorting algorithms and although it is not the most eficient it does the job and it is easy to understand and implement. It works by iterating multiple times through the array while checking, in each iteration, if each number is smaller than the one after. If they are not it swaps the two numbers. It stops when we have 0 swaps on the last iteration.

Example:

Starting point: unsorted

array = `[8,5,2,9,5,6,3]`

Iteration 1: 

array = `[5,2,8,5,6,3,9]`

Iteration 2: 

array = `[2,5,5,6,3,8,9]`

Iteration 3:

array = `[2,5,5,3,6,8,9]`

...

Final array: sorted

array = `[2,3,5,5,6,8,9]`

On each iteration we swap elements when the pointer is bigger than the pointer + 1. This goes on until we have an iteration with 0 swaps and then we know the array is completely sorted.


### Implementation 1

```python
def bubbleSort(array):
    isSorted = False 

    while isSorted == False:
        isSorted = True
        for i in range(len(array) - 1):
            if array[i] > array[i+1]:
                swap(i, i+1, array)
                isSorted = False
	return array

def swap(i, j, array):
    array[i], array[j] = array[j], array[i]
```

### Complexity Analysis

- Time Complexity: O(N^2), where N is the number of integers in the input array.

- Space Complexity: O(1). We use the same array that we were given by just swaping some numbers.

#

### Approach 2 (optimized)

If we take a look at the different iterations we can see that the biggest number always ends up at the end. Knowing this we can just create a counter and avoid the already sorted part of the array. This does not change the time or space complexities but it is slightly better than the first approach.

### Implementation 2 

```python
def bubbleSort(array):
    isSorted = False 
    counter = 0
    while isSorted == False:
        isSorted = True
        for i in range(len(array) - 1 - counter):
            if array[i] > array[i+1]:
                swap(i, i+1, array)
                isSorted = False
        counter += 1
	return array

def swap(i, j, array):
    array[i], array[j] = array[j], array[i]
```

### Complexity Analysis

- Time Complexity: O(N^2), where N is the number of integers in the input array.

- Space Complexity: O(1). We use the same array that we were given by just swaping some numbers.

#